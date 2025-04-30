# Cómo empezar

Esta guía de inicio rápido te permitirá realizar tu primera solicitud a la API en pocos minutos. A continuación, te llevaremos paso a paso por el proceso de configuración, autenticación y realización de una llamada básica.

### 1. Crea tu cuenta y obtener las credenciales de la API

Antes de comenzar, necesitarás una cuenta registrada.

### 2. Selecciona entorno

* Comienza en el entorno de pruebas (**Sandbox**), donde puedes testear sin afectar datos reales:

```
https://sandbox.emify.co/
```

* Una vez que tu implementación esté lista, solicita acceso al entorno de **Producción**.

### 3. Genera un bearer token

Para acceder a la API, todas las solicitudes deben incluir el Bearer Token en el encabezado de la solicitud. Para obtenerlo, tenés que usar el endpoint de Login:

```json
curl --location 'https://sandbox.emify.co/api/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email":"email@example.com",
    "password":"123456"
}'
```

### 4. Crea tu primera empresa:

Una vez autenticado, podrás crear una empresa para obtener una API Key y realizar operaciones con esta. Para más información, consultar la sección [Cómo dar de alta una empresa.](../como-dar-de-alta-una-empresa.md)

### **5. Explora otros Endpoints:**

Con tu API Key puedes explorar los demás endpoints disponibles en la sección de [`Referencias API`](../refencias-api/). Allí encontrarás detalles sobre cómo acceder a diferentes recursos y realizar operaciones más avanzadas.

### 6. Soporte:

Si encuentras algún problema o tienes preguntas, revisa nuestra sección de preguntas frecuentes o contacta a nuestro equipo de soporte.
