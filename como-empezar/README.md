# Cómo empezar

Esta guía de inicio rápido te permitirá realizar tu primera solicitud a la API en pocos minutos. A continuación, te llevaremos paso a paso por el proceso de configuración, autenticación y realización de una llamada básica.

#### 1. Obtener las Credenciales de la API

Antes de comenzar, necesitarás una cuenta registrada y obtener un Bearer Token. Sigue estos pasos:

1. **Registro**: para registrar una cuenta, puedes hacerlo desde nuestra plataforma.
2. **Generar Bearer Token**: Una vez registrado, puedes generar el Token a través de Login.

#### 2. Seleccionar entorno:

* Producción: es el ambiente para gestionar tus operaciones diarias y generan comprobantes válidos ante el organismo. Para usar este entorno, configurar `url_base: https://emify.com/`.
* Sandbox: es un ambiente de pruebas que se puede utilizar para probar el flujo de creación de empresas y emisión e impresión de comprobantes. Los comprobantes generados en este ambiente no son válidos ante el organismo. Para usar este entorno, configurar `url_base: https://sandbox.emify.com/`

#### 4. Autenticación

Para acceder a la API, todas las solicitudes deben incluir el Bearer Token en el encabezado de la solicitud. Aquí te mostramos un ejemplo utilizando `cURL`:

```bash
curl --location 'https://facttuapi.contabilium.com/api/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email":"email@example.com",
    "password":"123456"
}'
```

#### 5. Dar de alta una empresa:

Una vez autenticado, podrás crear una empresa para obtener una API Key y realizar operaciones con esta. Para más información, consultar la sección Cómo dar de alta una empresa.

#### 6. Explora los Endpoints:

Con tu API Key puedes explora los demás endpoints disponibles en la sección de Referencias API. Allí encontrarás detalles sobre cómo acceder a diferentes recursos y realizar operaciones más avanzadas.

#### 6. Soporte:

Si encuentras algún problema o tienes preguntas, revisa nuestra sección de preguntas frecuentes o contacta a nuestro equipo de soporte.
