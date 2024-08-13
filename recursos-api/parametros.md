---
hidden: true
---

# Parámetros



<table data-full-width="true"><thead><tr><th>Tabla de contenido</th></tr></thead><tbody><tr><td><a href="parametros.md#currencies">Currencies</a></td></tr><tr><td>Countries</td></tr><tr><td>Payment Type</td></tr><tr><td>Legal Entity</td></tr><tr><td>Tax Identification Documents</td></tr><tr><td>Document Type</td></tr><tr><td>Additional Export Info</td></tr><tr><td>Tax Types</td></tr><tr><td>Item Additional Info</td></tr><tr><td>Tax Information</td></tr><tr><td>Item Code Type</td></tr></tbody></table>

***

## Currencies

### Consultar moneda

<mark style="color:green;">`GET`</mark> `/currencies`

Este punto de acceso te permite obtener información de todas o una de las monedas con la opción de filtrar por su estado o código ISO del país.

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Query Params**

<table data-full-width="true"><thead><tr><th>Parámetro</th><th>Descripción</th><th data-hidden>Type</th></tr></thead><tbody><tr><td>id</td><td>ID de la moneda</td><td>string</td></tr><tr><td>estado</td><td>Estado de la moneda</td><td>number</td></tr><tr><td>codigo_iso</td><td>Código ISO del país</td><td></td></tr></tbody></table>

**Respuesta**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "id": integer,
        "id_country": string,
        "description": string,
        "currency_code": string,
        "iso_code": string,
        "agency_code": string,
        "state": string
    }
]
```
{% endtab %}
{% endtabs %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá una matriz de objetos de moneda, cada uno con las siguientes propiedades:&#x20;

* id: el ID de la moneda.
* id\_country: el ID del país asociado con la moneda.
* description: la descripción de la moneda.
* currency\_code: el código de la moneda.
* iso\_code: el código ISO de la moneda.
* agency\_code: el código de la agencia de la moneda.
* state: el estado de la moneda.

***

## Locations

{% tabs %}
{% tab title="Regions" %}
### Consultar región / provincia / departamento / estado

<mark style="color:green;">`GET`</mark> `api/regions`

Este punto de acceso te permite obtener información sobre las regiones de un país específico.

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Query Params**

<table data-full-width="true"><thead><tr><th>Parámetro</th><th>Descripción</th><th data-hidden>Type</th></tr></thead><tbody><tr><td>id_country</td><td>ID del país consultado (requerido)</td><td>number</td></tr></tbody></table>

**Respuesta**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "id": integer,
        "id_country": integer,
        "nombre": string
    }
]
```
{% endtab %}
{% endtabs %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de regiones, cada uno con las siguientes propiedades:&#x20;

* id: ID de la región.
* id\_country: el ID del país consultado.
* nombre: nombre de la región.
{% endtab %}

{% tab title="Countries" %}
### Consultar países

<mark style="color:green;">`GET`</mark> `api/countries`

Este punto de acceso te permite obtener información de todos los países.

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Respuesta**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "id": 4,
        "nombre": string,
        "iso3": "URY"
    }
]
```
{% endtab %}
{% endtabs %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de países, cada uno con las siguientes propiedades:&#x20;

* id: ID del país..
* nombre: nombre del país.
* iso3: código ISO 3166-1 alfa-3.
{% endtab %}
{% endtabs %}

***

### Payment Types

### Consultar tipo de pagos

<mark style="color:green;">`GET`</mark> `api/payment-types`

Este punto de acceso te permite obtener todas las forma de pago posibles con la posibilida de filtrar por país y estado de activación.

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Query Params**

<table data-full-width="true"><thead><tr><th>Parámetro</th><th>Descripción</th><th data-hidden>Type</th></tr></thead><tbody><tr><td>id_country</td><td>ID del país consultado</td><td>number</td></tr><tr><td>state</td><td>Estado del tipo de pago</td><td></td></tr></tbody></table>

**Respuesta**

{% tabs %}
{% tab title="200" %}
<pre class="language-json"><code class="lang-json">[
 {
        "id": integer,
        "id_country": integer,
        "description": string,
        "code": string,
        "agency_code": string,
        "state": string
    }
<strong>]
</strong></code></pre>
{% endtab %}
{% endtabs %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de formas de pago, cada uno con las siguientes propiedades:&#x20;

* id: ID de la forma de pago.
* id\_country: ID del país asociado a la forma de pago.
* descripción: nombre de la forma de pago.
* agency\_code:
* state: estado de la forma de pago.

***

### Legal Entity

### Consultar personería

<mark style="color:green;">`GET`</mark> `api/legal-entities`

Este punto de acceso te permite obtener todas o una de los tipos de persona (representación legal) con la opción de filtrar por país o estado.

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Query Params**

<table data-full-width="true"><thead><tr><th>Parámetro</th><th>Descripción</th><th data-hidden>Type</th></tr></thead><tbody><tr><td>id</td><td>ID del tipo de persona</td><td></td></tr><tr><td>id_country</td><td>ID del país consultado</td><td>number</td></tr><tr><td>state</td><td>Estado del tipo de persona</td><td></td></tr></tbody></table>

**Respuesta**

{% tabs %}
{% tab title="200" %}
<pre class="language-json"><code class="lang-json">[
 {
        "id": integer,
        "id_country": integer,
        "description": string,
        "code": string,
        "agency_code": string,
        "state": string
    }
<strong>]
</strong></code></pre>
{% endtab %}
{% endtabs %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de tipos de persona, cada uno con las siguientes propiedades:&#x20;

* id: ID del tipo de persona.
* id\_country: ID del país asociado al tipo de persona.
* descripción: nombre del tipo de persona.
* agency\_code:
* state: estado del tipo de persona.

***

### Measurement Units

### Consultar unidades de medidas

<mark style="color:green;">`GET`</mark> `api/measurement-units`

Este punto de acceso te permite obtener todas o una de las unidades de medidas utilizadas en comprobantes con la opción de filtrar por país o estado.

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Query Params**

<table data-full-width="true"><thead><tr><th>Parámetro</th><th>Descripción</th><th data-hidden>Type</th></tr></thead><tbody><tr><td>id</td><td>ID de la unidad de medida</td><td></td></tr><tr><td>id_country</td><td>ID del país consultado</td><td>number</td></tr><tr><td>state</td><td>Estado de la unidad de medida</td><td></td></tr></tbody></table>

**Respuesta**

{% tabs %}
{% tab title="200" %}
<pre class="language-json"><code class="lang-json">[
 {
        "id": integer,
        "id_country": integer,
        "description": string,
        "code": string,
        "agency_code": string,
        "state": string
    }
<strong>]
</strong></code></pre>
{% endtab %}
{% endtabs %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de unidades de medidas, cada uno con las siguientes propiedades:&#x20;

* id: ID de la unidad de medida.
* id\_country: ID del país asociado a la unidad de medida.
* descripción: nombre de de la unidad de medida.
* agency\_code:
* state: estado de la unidad de medida.

***

### Tax Identification Documents

### Consultar tipo de documento

<mark style="color:green;">`GET`</mark> `api/tax-identification-documents`

Este punto de acceso te permite obtener todas o una de los tipo de documentos utilizados en comprobantes con la opción de filtrar por país o estado.

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Query Params**

<table data-full-width="true"><thead><tr><th>Parámetro</th><th>Descripción</th><th data-hidden>Type</th></tr></thead><tbody><tr><td>id</td><td>ID del tipo de documento</td><td></td></tr><tr><td>id_country</td><td>ID del país consultado</td><td>number</td></tr><tr><td>state</td><td>Estado del tipo de documento</td><td></td></tr></tbody></table>

**Respuesta**

{% tabs %}
{% tab title="200" %}
<pre class="language-json"><code class="lang-json">[
 {
        "id": integer,
        "id_country": integer,
        "description": string,
        "code": string,
        "agency_code": string,
        "state": string
    }
<strong>]
</strong></code></pre>
{% endtab %}
{% endtabs %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de tipos de documentos, cada uno con las siguientes propiedades:&#x20;

* id: ID de tipos de documentos.
* id\_country: ID del país asociado al tipo de documento.
* descripción: nombre del tipo de documento.
* agency\_code: código del organismo para identificar el tipo de documento.
* state: estado del tipo de documento.

***

### Tax Identification Documents

### Consultar tipo de comprobante

<mark style="color:green;">`GET`</mark> `api/document-`

Este punto de acceso te permite obtener todas o una de los tipo de comprobantes utilizados con la opción de filtrar por país o estado.

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Query Params**

<table data-full-width="true"><thead><tr><th>Parámetro</th><th>Descripción</th><th data-hidden>Type</th></tr></thead><tbody><tr><td>id</td><td>ID del tipo de comprobante</td><td></td></tr><tr><td>id_country</td><td>ID del país</td><td>number</td></tr><tr><td>state</td><td>Estado del comprobante</td><td></td></tr></tbody></table>

**Respuesta**

{% tabs %}
{% tab title="200" %}
<pre class="language-json"><code class="lang-json">[
 {
        "id": integer,
        "id_country": integer,
        "description": string,
        "code": string,
        "agency_code": string,
        "state": string
    }
<strong>]
</strong></code></pre>
{% endtab %}
{% endtabs %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de tipos de comprobantes, cada uno con las siguientes propiedades:&#x20;

* id: ID de tipos de comprobantes.
* id\_country: ID del país asociado al tipo de comprobante.
* descripción: nombre del tipo de comprobante.
* agency\_code: código del organismo para identificar el tipo de comprobante.
* state: estado del tipo de comprobante.

***

### Additional Export Info

### Consultar datos adicionales para enviar

<mark style="color:green;">`GET`</mark> `api/additional-export-info`

Este punto de acceso te permite obtener todos o uno de los datos adicionales que se pueden enviar  con la opción de filtrar por país o estado.

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Query Params**

<table data-full-width="true"><thead><tr><th>Parámetro</th><th>Descripción</th><th data-hidden>Type</th></tr></thead><tbody><tr><td>id</td><td>ID del dato</td><td></td></tr><tr><td>id_country</td><td>ID del país</td><td>number</td></tr><tr><td>state</td><td>Estado del dato</td><td></td></tr></tbody></table>

**Respuesta**

{% tabs %}
{% tab title="200" %}
<pre class="language-json"><code class="lang-json">[
 {
        "id": integer,
        "id_country": integer,
        "key": string,
        "data_type": string,
        "description": string,
        "state": string
    }
<strong>]
</strong></code></pre>
{% endtab %}
{% endtabs %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de los tipos de datos adicionales, cada uno con las siguientes propiedades:&#x20;

* id: ID de los datos.
* id\_country: ID del país asociado al dato.
* descripción: nombre del dato.
* agency\_code: código del organismo para identificar el dato.
* state: estado del dato.

***

### Tax Types

### Consultar datos adicionales para enviar

<mark style="color:green;">`GET`</mark> `api/tax-types`

Este punto de acceso te permite obtener todos o uno de los tipos de impuestos con la opción de filtrar por país o estado.

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Query Params**

<table data-full-width="true"><thead><tr><th>Parámetro</th><th>Descripción</th><th data-hidden>Type</th></tr></thead><tbody><tr><td>id</td><td>ID del impuesto</td><td></td></tr><tr><td>id_country</td><td>ID del país</td><td>number</td></tr><tr><td>state</td><td>Estado del impuesto</td><td></td></tr></tbody></table>

**Respuesta**

{% tabs %}
{% tab title="200" %}
<pre class="language-json"><code class="lang-json">[
 {
        "id": integer,
        "id_country": integer,
        "key": string,
        "data_type": string,
        "description": string,
        "state": string
    }
<strong>]
</strong></code></pre>
{% endtab %}
{% endtabs %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de los tipos de datos adicionales, cada uno con las siguientes propiedades:&#x20;

* id: ID de los datos.
* id\_country: ID del país asociado al dato.
* descripción: nombre del dato.
* agency\_code: código del organismo para identificar el dato.
* state: estado del dato.
