# Emisión e Impresión

Esta sección agrupa todos aquellos endpoints para la creación, obtención de comprobantes e impresión de comprobantes. Para el caso de la creación de comprobantes, se muestra una descripción detalladas del body request debajo de la referencia del endpoint.

### GET Invoice - Descripción del body response

El significado de las propiedades en las respuestas coinciden con las que se encuentran en el cuerpo de la petición, sin embargo hay algunas nuevas propiedades que se presentan a continuación:

* **id** (`string`): Identificador único de la factura.
* **`number`**`(string)`: Representa el número único del comprobante emitido (e.g., "0001-00012345").&#x20;
* Electronica Authorization:
  * **type** (`null` o `string`): Tipo de autorización electrónica.
  * **code** (`null` o `string`): Código de la autorización electrónica.
  * **expiration\_date** (`null` o `string`): Fecha de expiración de la autorización.
  * **qr** (`null` o `string`): Información del código QR.
  * **additional\_info** (`null` o `string`): Información adicional de la autorización.

<figure><img src="../.gitbook/assets/estados (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Status**

* "Pending": el comprobante está pendiente por ser procesado.
* "In process": el comprobante se encuentra esperando respuesta del ente fiscal.
* "Accepted": el comprobante se encuentra aceptado y exitosamente emitido al ente fiscal.
* "Rejected": el comprobante se encuentra rechazado. Ver motivo.
{% endhint %}

### POST Invoice - Descripción del body request

A continuación se indica el tipo de dato y la descripción de los parámetros que se envían en la petición.  Las propiedades obligatorias están indicadas con asterisco (\*).

<details>

<summary>Invoice base data</summary>

* <mark style="color:red;">\*</mark>**branch\_office** (integer): ID de la sucursal desde la que se emite el comprobante.
* <mark style="color:red;">\*</mark>[**invoice\_type** (string)](parametros.md#api-document-types): Tipo de comprobante, en este caso "FCA" (Factura A).
* <mark style="color:red;">\*</mark>**invoice\_date** (string, formato datetime): Fecha en la que se emite el comprobante. Formato "DD-MM-YYYY".
* <mark style="color:red;">\*</mark>**payment\_due\_date** (string, formato date): Fecha de vencimiento del pago. Formato "DD-MM-YYYY". No puede ser anterior a **invoice\_date.**
* **service\_start\_date** (string, formato datetime): Fecha de inicio de la prestación del servicio. Formato "DD-MM-YYYY". Requerido cuando **concept** es 2 o 3.
* **service\_end\_date** (string, formato datetime): Fecha de finalización de la prestación del servicio. Formato "DD-MM-YYYY". Requerido cuando **concept** es 2 o 3. No puede ser anterior a **service\_start\_date.**
* **concept** (string): Concepto del comprobante. Se utiliza para clasificar el tipo de transacción. Valores posibles: "1": Productos, "2": Servicios, "3": Productos y servicios. Requerido para emisión Argentina.
* **observations** (string): Observaciones adicionales que se deseen agregar en el comprobante.
* **external\_reference** (string): Referencia externa que se puede utilizar para identificar el comprobante en sistemas externos. Es un valor único para cada comprobante, por lo tanto, la petición responde con error en caso de enviar una valor que se encuentra asociado a otro comprobante.
* **reason\_code** (`null` o `string`): Código para identificar la razón de cancelación de un comprobante. Solo se muestra para Notas de Crédito. Puede ser `null`.

- [**currency**](parametros.md#api-currencies):
  * <mark style="color:red;">\*</mark>**code** (string): Código de la moneda utilizada (por ejemplo, ARS para pesos argentinos).
  * <mark style="color:red;">\*</mark>**exchange\_rate** (float): Tasa de cambio aplicada en la transacción (1 si es la moneda local).
- [**payment\_method**](parametros.md#api-payment-types):
  * <mark style="color:red;">\*</mark>**code** (string): Código del método de pago (por ejemplo, "CON" para cuenta corriente).

</details>

<details>

<summary>Issuer &#x26; Recipient</summary>

* <mark style="color:red;">\*</mark>**legal\_name** (string): Nombre legal del emisor/receptor del comprobante.
* <mark style="color:red;">\*</mark>[**document\_type** (string)](parametros.md#api-tax-identification-documents): Tipo de documento del emisor/receptor (por ejemplo, DNI).
* <mark style="color:red;">\*</mark>**document\_number** (string): Número de documento del emisor/receptor.
* <mark style="color:red;">\*</mark>**address**: Información de la dirección del emisor.
  * <mark style="color:red;">\*</mark>[**country** (string)](parametros.md#api-countries): País.
  * <mark style="color:red;">\*</mark>[**state** (string)](parametros.md#api-regions): Estado o provincia.
  * <mark style="color:red;">\*</mark>**address** (string): Dirección.
  * **phone** (string): Teléfono de contacto.
* [**tax\_information** (object, nullable)](parametros.md#api-tax-information): Información impositiva del emisor/receptor, si es aplicable, como por ejemplo fecha de inicio de actividades o correo electrónico.

</details>

<details>

<summary>Items</summary>

**items** (array): Lista de los productos o servicios incluidos en el comprobante. Todos los importes se consideran aplicados a una unidad. Cada ítem contiene:

* <mark style="color:red;">\*</mark>**quantity** (integer): Cantidad del producto o servicio.
* [**code\_unit\_of\_measure** (string)](parametros.md#api-measurement-units): Código de la unidad de medida (por ejemplo, "u" para unidad).
* **discount\_amount** (float): Monto de descuento aplicado al ítem .
* <mark style="color:red;">\*</mark>**unit\_price** (float): Precio unitario del ítem sin impuestos.
* **description** (string): Descripción del ítem.
* [**code**](parametros.md#api-item-code-types): Código del producto o servicio:
  * **type** (string): Tipo de código (por ejemplo, "sku").
  * **value** (string): Valor del código del ítem.
* <mark style="color:red;">\*</mark>[**taxes** (array)](parametros.md#api-tax-types): Lista de impuestos aplicados al ítem. Cada impuesto incluye:
  * **type** (string): Código del tipo de impuesto (por ejemplo, "iva21" para IVA al 21%).
  * **amount** (float): Monto del impuesto.
  * **rate** (float): Tasa de impuesto aplicable.

</details>

<details>

<summary>Totals</summary>

* <mark style="color:red;">\*</mark>**sub\_total** (float): Subtotal de la transacción antes de impuestos y descuentos.
* **discount** (float): Monto total de descuentos aplicados. Debe coincidir con la sumatoria de los descuentos totales de los ítems.
* <mark style="color:red;">\*</mark>[**taxes** (array)](parametros.md#api-tax-types): Lista de impuestos totales aplicados al comprobante. Cada impuesto incluye:
  * **type** (string): Código del tipo de impuesto (por ejemplo, "iva21").
  * **amount** (float): Monto total del impuesto.
  * **base\_amount** (float): Monto base sobre el cual se calcula el impuesto.
* <mark style="color:red;">\*</mark>**total** (float): Total final a pagar, incluyendo impuestos y descuentos.

</details>

<details>

<summary>Global Taxes</summary>

El array `global_taxes` contiene información sobre los impuestos aplicados globalmente sobre el comprobante (Ejemplo: IIBB para Argentina). Cada objeto dentro del array representa un tipo de impuesto aplicado.

| Campo         | Descripción                                                                                                                          |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| `type`        | Tipo de impuesto aplicado. Solo se permiten los valores de `code` del recurso [Tax Type ](parametros.md#api-tax-types)en Parámetros. |
| `base_amount` | Monto de la base imponible sobre la cual se calculan los impuestos globales.                                                         |
| `amount`      | Monto total del impuesto aplicado.                                                                                                   |
| `rate`        | Porcentaje del impuesto que se aplica, el cual debe coincidir con los valores de `rate` en `tax_types` y corresponder con `type.`    |

</details>

<details>

<summary>Additional Header Info</summary>

[Ver en Parámetros.](emision-e-impresion.md#additional-header-info)

</details>

<details>

<summary>Additional Export Info</summary>

[Ver en Parámetros.](emision-e-impresion.md#additional-export-info)

</details>

{% openapi src="../.gitbook/assets/create_invoice (2).yaml" path="/api/invoices" method="post" %}
[create_invoice (2).yaml](<../.gitbook/assets/create_invoice (2).yaml>)
{% endopenapi %}

{% openapi src="../.gitbook/assets/getInvoice.yaml" path="/api/invoices/{{invoice_id}}" method="get" %}
[getInvoice.yaml](../.gitbook/assets/getInvoice.yaml)
{% endopenapi %}

Anulación rápida de comprobante. Genera una nota de crédito a partir de un ID comprobante

{% openapi src="../.gitbook/assets/NC_yaml.yaml" path="/api/invoices/{{invoice_id}}/void" method="delete" %}
[NC_yaml.yaml](../.gitbook/assets/NC_yaml.yaml)
{% endopenapi %}

{% openapi src="../.gitbook/assets/pdf_yaml.yaml" path="/api/invoices/{{invoice_id}}/download-pdf/A4" method="post" %}
[pdf_yaml.yaml](../.gitbook/assets/pdf_yaml.yaml)
{% endopenapi %}

{% openapi src="../.gitbook/assets/pdf_yaml.yaml" path="/api/invoices/{{invoice_id}}/download-pdf/58mm" method="post" %}
[pdf_yaml.yaml](../.gitbook/assets/pdf_yaml.yaml)
{% endopenapi %}

{% openapi src="../.gitbook/assets/XML_facttu.yaml" path="/api/invoices/{{invoice_id}}/download/xml" method="post" %}
[XML_facttu.yaml](../.gitbook/assets/XML_facttu.yaml)
{% endopenapi %}



