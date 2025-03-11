# Parámetros

Esta es una sección de consulta que tiene el objetivo de agrupar todos aquellos parámetros  que se usan en la petición de emisión de comprobantes. La obligatoriedad de estos parámetros dependen del tipo de comprobante. En cada petición podrás filtrar por `id_country` para obtener información relacionada al país de tu interés. Todos los endpoints utilizan el Bearer Token generado a través del Login como método de autenticación.



{% openapi src="../.gitbook/assets/additiona_export_info.yaml" path="/api/additional-export-info" method="get" %}
[additiona_export_info.yaml](../.gitbook/assets/additiona_export_info.yaml)
{% endopenapi %}

### Additional Header Info

El array `additional_header_info` permite agregar datos complementarios a la solicitud dependiendo del comprobante a emitir y la normativa del país.

#### **Estructura genérica del JSON**

```bash
{
  "additional_header_info": {
    "seller_name": "Nombre del vendedor", 
    "seller_email": "vendedor@email.com",
    "bank_account": "Cuenta bancaria asociada (Argentina)",
    "IndTraslado": "Indicador de traslado (Uruguay)",
    "NroInterno": "Número interno de referencia (Uruguay)",
    "ModVenta": "Modalidad de venta (Uruguay)",
    "ViaTransp": "Vía de transporte (Uruguay)",
    "ClauVenta": "Cláusula de venta (Uruguay)",
    "IndServicio": 11111, (Chile) 
    "TipoTraslado": 22222, (Chile) 
    "TipoDespacho": 333333, (Chile) 
    "Transporte": {
      "Patente": "ABC123", 
      "RUTTrans": "12345678-9", 
      "RUTChofer": "87654321-0", 
      "NombreChofer": "Juan Pérez" 
    } (Chile) 
  }
}
```

#### **Consideraciones**

* `seller_name` y `seller_email` son obligatorios en todas las solicitudes.
* Los demás campos son opcionales y deben enviarse solo si aplican a tu operación.
* Los campos bajo `Transporte` deben incluirse solo si se trata de una operación con traslado de mercadería en Chile.
* Los campos de Uruguay aplican para e-remitos.
* Los campos específicos de Uruguay y Chile deben enviarse según el país correspondiente.
* Si un campo no es relevante para tu operación, simplemente omítelo en la solicitud.

{% openapi src="../.gitbook/assets/parametros.yaml" path="/api/countries" method="get" %}
[parametros.yaml](../.gitbook/assets/parametros.yaml)
{% endopenapi %}

{% openapi src="../.gitbook/assets/parametros.yaml" path="/api/currencies" method="get" %}
[parametros.yaml](../.gitbook/assets/parametros.yaml)
{% endopenapi %}

{% openapi src="../.gitbook/assets/parametros.yaml" path="/api/document-types" method="get" %}
[parametros.yaml](../.gitbook/assets/parametros.yaml)
{% endopenapi %}

### Document Cancellation Reason

Son los valores posibles que se envían en la generación de notas de crédito. En la sección de ejemplos se encuentra cómo enviar este valor a través de `reason_code.`

<table><thead><tr><th>País</th><th width="202">Descripción</th><th>Código</th></tr></thead><tbody><tr><td>Argentina</td><td>CORRIGE MONTOS</td><td>MON</td></tr><tr><td>Argentina</td><td>ANULA DOCUMENTO DE REFERENCIA</td><td>ANU</td></tr><tr><td>Chile</td><td>CORRIGE MONTOS</td><td>MON</td></tr><tr><td>Chile</td><td>CORRIGE TEXTO REFERENCIA</td><td>TEX</td></tr><tr><td>Chile</td><td>ANULA DOCUMENTO DE REFERENCIA</td><td>ANU</td></tr><tr><td>Uruguay</td><td>CORRIGE MONTOS</td><td>MON</td></tr><tr><td>Uruguay</td><td>CORRIGE TEXTO REFERENCIA</td><td>TEX</td></tr><tr><td>Uruguay</td><td>ANULA DOCUMENTO DE REFERENCIA</td><td>ANU</td></tr></tbody></table>

{% openapi src="../.gitbook/assets/parametros.yaml" path="/api/item-code-types" method="get" %}
[parametros.yaml](../.gitbook/assets/parametros.yaml)
{% endopenapi %}

***

***

{% openapi src="../.gitbook/assets/parametros.yaml" path="/api/legal-entities" method="get" %}
[parametros.yaml](../.gitbook/assets/parametros.yaml)
{% endopenapi %}

***

{% openapi src="../.gitbook/assets/parametros.yaml" path="/api/measurement-units" method="get" %}
[parametros.yaml](../.gitbook/assets/parametros.yaml)
{% endopenapi %}

***

{% openapi src="../.gitbook/assets/parametros.yaml" path="/api/payment-types" method="get" %}
[parametros.yaml](../.gitbook/assets/parametros.yaml)
{% endopenapi %}

{% openapi src="../.gitbook/assets/CountryRegionPayment.yaml" path="/api/regions" method="get" %}
[CountryRegionPayment.yaml](../.gitbook/assets/CountryRegionPayment.yaml)
{% endopenapi %}

{% openapi src="../.gitbook/assets/parametros.yaml" path="/api/tax-identification-documents" method="get" %}
[parametros.yaml](../.gitbook/assets/parametros.yaml)
{% endopenapi %}

***

***

{% openapi src="../.gitbook/assets/additiona_export_info.yaml" path="/api/tax-information" method="get" %}
[additiona_export_info.yaml](../.gitbook/assets/additiona_export_info.yaml)
{% endopenapi %}

{% openapi src="../.gitbook/assets/parametros.yaml" path="/api/tax-types" method="get" %}
[parametros.yaml](../.gitbook/assets/parametros.yaml)
{% endopenapi %}

***



