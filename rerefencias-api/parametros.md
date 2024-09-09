---
description: >-
  En esta sección, encontrarás los endpoints que te permiten realizar consultas
  rápidas y sencillas sobre parámetros clave dentro de nuestro sistema.
---

# Parámetros

{% swagger src="../.gitbook/assets/yaml2.yaml" path="/api/currencies" method="get" %}
[yaml2.yaml](../.gitbook/assets/yaml2.yaml)
{% endswagger %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá una matriz de objetos de moneda, cada uno con las siguientes propiedades:&#x20;

* id: el ID de la moneda.
* id\_country: el ID del país asociado con la moneda.
* description: la descripción de la moneda.
* currency\_code: el código de la moneda.
* iso\_code: el código ISO de la moneda.
* agency\_code: el código de la agencia de la moneda.
* state: el estado de la moneda.

***

{% swagger src="../.gitbook/assets/CountryRegionPayment.yaml" path="/api/countries" method="get" %}
[CountryRegionPayment.yaml](../.gitbook/assets/CountryRegionPayment.yaml)
{% endswagger %}

***

{% swagger src="../.gitbook/assets/CountryRegionPayment.yaml" path="/api/regions" method="get" %}
[CountryRegionPayment.yaml](../.gitbook/assets/CountryRegionPayment.yaml)
{% endswagger %}

***

{% swagger src="../.gitbook/assets/CountryRegionPayment.yaml" path="/api/payment-types" method="get" %}
[CountryRegionPayment.yaml](../.gitbook/assets/CountryRegionPayment.yaml)
{% endswagger %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de formas de pago, cada uno con las siguientes propiedades:&#x20;

* id: ID de la forma de pago.
* id\_country: ID del país asociado a la forma de pago.
* descripción: nombre de la forma de pago.
* agency\_code:
* state: estado de la forma de pago.

***



{% swagger src="../.gitbook/assets/yaml3.yaml" path="/api/legal-entities" method="get" %}
[yaml3.yaml](../.gitbook/assets/yaml3.yaml)
{% endswagger %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de tipos de persona, cada uno con las siguientes propiedades:&#x20;

* id: ID del tipo de persona.
* id\_country: ID del país asociado al tipo de persona.
* descripción: nombre del tipo de persona.
* agency\_code:
* state: estado del tipo de persona.

***

{% swagger src="../.gitbook/assets/mesearument.yaml" path="/api/measurement-units" method="get" %}
[mesearument.yaml](../.gitbook/assets/mesearument.yaml)
{% endswagger %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de unidades de medidas, cada uno con las siguientes propiedades:&#x20;

* id: ID de la unidad de medida.
* id\_country: ID del país asociado a la unidad de medida.
* descripción: nombre de de la unidad de medida.
* agency\_code:
* state: estado de la unidad de medida.

***

{% swagger src="../.gitbook/assets/mesearument.yaml" path="/api/document-types" method="get" %}
[mesearument.yaml](../.gitbook/assets/mesearument.yaml)
{% endswagger %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de tipos de documentos, cada uno con las siguientes propiedades:&#x20;

* id: ID de tipos de documentos.
* id\_country: ID del país asociado al tipo de documento.
* descripción: nombre del tipo de documento.
* agency\_code: código del organismo para identificar el tipo de documento.
* state: estado del tipo de documento.

***

{% swagger src="../.gitbook/assets/mesearument.yaml" path="/api/tax-information" method="get" %}
[mesearument.yaml](../.gitbook/assets/mesearument.yaml)
{% endswagger %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de tipos de comprobantes, cada uno con las siguientes propiedades:&#x20;

* id: ID de tipos de comprobantes.
* id\_country: ID del país asociado al tipo de comprobante.
* descripción: nombre del tipo de comprobante.
* agency\_code: código del organismo para identificar el tipo de comprobante.
* state: estado del tipo de comprobante.

***

{% swagger src="../.gitbook/assets/mesearument.yaml" path="/api/additional-export-info" method="get" %}
[mesearument.yaml](../.gitbook/assets/mesearument.yaml)
{% endswagger %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de los tipos de datos adicionales, cada uno con las siguientes propiedades:&#x20;

* id: ID de los datos.
* id\_country: ID del país asociado al dato.
* descripción: nombre del dato.
* agency\_code: código del organismo para identificar el dato.
* state: estado del dato.

***

{% swagger src="../.gitbook/assets/mesearument.yaml" path="/api/tax-types" method="get" %}
[mesearument.yaml](../.gitbook/assets/mesearument.yaml)
{% endswagger %}

La respuesta tendrá un código de estado de 200 y un tipo de contenido de aplicación/json. El cuerpo de la respuesta contendrá un arreglo de objetos de los tipos de datos adicionales, cada uno con las siguientes propiedades:&#x20;

* id: ID de los datos.
* id\_country: ID del país asociado al dato.
* descripción: nombre del dato.
* agency\_code: código del organismo para identificar el dato.
* state: estado del dato.

***

{% swagger src="../.gitbook/assets/mesearument.yaml" path="/api/item-code-types" method="get" %}
[mesearument.yaml](../.gitbook/assets/mesearument.yaml)
{% endswagger %}
