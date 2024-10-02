# Cómo dar de alta una empresa

Con esta guía podrás dar de alta una nueva empresa, cargar su certificado y logo, además de ajustar numeración de comprobantes.

#### **1. Autenticarte**

Para acceder a la API, todas las solicitudes deben incluir el Bearer Token en el encabezado de la solicitud. Aquí te mostramos un ejemplo utilizando `cURL`:

```batch
curl --request POST '{{base_url}}/api/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email":"email@example.com",
    "password":"123456"
}'
```

#### **2. Crear una empresa**

Ya autenticado, podrás crear una empresa y obtener un `id_company` con el siguiente recurso:

```batch
curl --resquest POST '{{base_url}}/api/companies' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer abcd' \
--data '{
    "legal_name":"Chile SRL",
    "tax_identifier":"434234",
    "tax_identifier_name":"RUT",
    "start_activities_date":"2023-01-01",
    "id_currency" : 5
}'
```

#### **3. Genera una API Key para la empresa**

Para operar con tu empresa necesitas generar una API Key a través de la siguiente petición:

```batch
curl --request POST '{{base_url}}/api/companies/apikey' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer abcd' \
--data '{
    "id_company": "36",
    "description": "key para empresa"
}'
```

{% hint style="warning" %}
Guarda tu API Key, ya que no podrás consultarla en otro momento.
{% endhint %}

#### **4. Cargar logo**

Ahora ya podrás cargar un logo de la empresa:

```batch
curl --request POST '{{base_url}}/api/companies/{{id_company}}/logo' \
--header 'x-api-key: abcd' \
--form 'logo=@"/C:/Users/Empresa/Descargas/logo-example.jpg"'
```

#### **5. Cargar certificado**

A tu empresa tendrás que cargar certificado de facturación electrónica para comenzar a operar:

```batch
curl --request POST '{{base_url}}/api/companies/{{id_empresa}}/certificates' \
--header 'x-api-key: abcd' \
--form 'from_date="2023-03-23"' \
--form 'expiration_date="2025-03-22"' \
--form 'password="abcdef"' \
--form 'environment="Production"' \
--form 'certificate=@"/C:/Users/Empresa/Descargas/CertificadoTest.pfx"'
```

#### **6. Cargar numeración**  :flag\_cl: :flag\_uy:

El siguiente paso es cargar el rango de numeración para operar con cada tipo de comprobante:

```batch
curl --request POST '{{base_url}}/api/companies/{{id_empresa}}/enumeration/upload' \
--header 'x-api-key: abcd' \
--form 'id_document_type="55"' \
--form 'file=@"/C:/Users/Empresa/Downloads/Ejemplo.xml"'
```

El ID en la respuesta corresponde con `id_enumeration` que se encuentra vinculado a un tipo de comprobante.

#### **7. Configurar numeración**  :flag\_cl: :flag\_uy:

Una vez cargado el archivo con el rango de numeración, es necesario configurarlo para cada tipo de comprobante a partir del `id_enumeration`. En caso de saltarse este paso, la numeración inicial será correspondiente al límite inferior del rango cargado:

```batch
curl --request PUT '{{base_url}}/api/companies/{{id_empresa}}/enumeration/{{id_enumeration}}/config' \
--header 'Content-Type: application/json' \
--header 'x-api-key: abcd' \
--data '{
    "enumeration_starts_from" : 5201
}'
```

{% hint style="info" %}
* La configuración de la enumeración se hace por cada tipo de comprobante.
* Configurar la enumeración es necesario cuando has facturado con otros servicios con el objetivo de respetar la correlatividad de tus comprobantes a lo largo de todos sistemas que has usado.
{% endhint %}

#### **8. Configurar webhooks**

Por último, opcionalmente puedes configurar webhooks para recibir notificaciones.
