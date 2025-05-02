# Cómo empezar

Esta guía de inicio rápido te permitirá realizar tu primera solicitud a la API en pocos minutos. A continuación, te llevaremos paso a paso por el proceso de configuración, autenticación y realización de una llamada básica.

### 1. Crear tu cuenta y obtener las credenciales de la API

Antes de comenzar, necesitás una cuenta registrada en nuestra plataforma. Una vez registrado, podrás autenticarte y operar desde el entorno de pruebas.

### 2. Seleccionar entorno

* Comienza en el entorno de pruebas (**Sandbox**), donde puedes testear sin afectar datos reales:

```
https://sandbox.emify.co/
```

* Una vez que tu implementación esté lista, solicita acceso al entorno de **Producción**.

### 3. Generar un bearer token

Para autenticarte, necesitás generar un Bearer Token. Este token se usa en todas las llamadas iniciales a la API, incluyendo la creación de empresas.

**Ejemplo:**

```json
--location 'https://sandbox.emify.co/api/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email": "email@example.com",
    "password": "123456"
}'
```

La respuesta incluirá un token similar a este:

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6..."
}
```

### 4. Hacer tu primera llamada autenticada

Ahora que tenés tu token, podés comenzar a interactuar con la API.

**Por ejemplo, obtener el listado de empresas asociadas:**

```json
--location 'https://sandbox.emify.co/api/companies' \
--header 'Authorization: Bearer TU_TOKEN'
```

### 5. Crear tu primera empresa:

Una vez autenticado, podrás crear una empresa para obtener una API Key y realizar operaciones con esta. Para más información, consultar la sección [Cómo dar de alta una empresa.](../como-dar-de-alta-una-empresa.md)

### 5. ¿Token o API Key?

* El **Bearer Token** te permite autenticarte como usuario y crear empresas.
* La **API Key** se genera para cada empresa y se usa para emitir comprobantes, cargar certificados, numeración, etc.

### **6. Explorar otros Endpoints:**

Con tu API Key puedes explorar los demás endpoints disponibles en la sección de [`Referencias API`](../refencias-api/). Allí encontrarás detalles sobre cómo acceder a diferentes recursos y realizar operaciones más avanzadas.

### 7. Soporte:

Si encuentras algún problema o tienes preguntas, revisa nuestra sección de preguntas frecuentes o contacta a nuestro equipo de soporte.
