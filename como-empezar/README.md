# Cómo empezar

Esta guía de inicio rápido te permitirá realizar tu primera solicitud a la API en pocos minutos. A continuación, te llevaremos paso a paso por el proceso de configuración, autenticación y realización de una llamada básica.

#### 1. Obtener las Credenciales de la API

Antes de comenzar, necesitarás una cuenta registrada y obtener un Bearer Token. Sigue estos pasos:

1. **Registro**: para registrar una cuenta, puedes hacerlo desde nuestra plataforma.
2. **Generar Bearer Token**: Una vez registrado, puedes generar el Token a través de Login.

#### 2. Autenticación

Para acceder a la API, todas las solicitudes deben incluir el Bearer Token en el encabezado de la solicitud. Aquí te mostramos un ejemplo utilizando `cURL`:

```bash
bashCopiar códigocurl -X GET "{{url}}/v1/ejemplo" \
-H "Authorization: Bearer TU_TOKEN"
```

#### 3. Realizar tu Primera Solicitud

Para realizar tu primera solicitud, prueba el siguiente endpoint que devuelve información básica de tu cuenta:

```bash
bashCopiar códigocurl -X GET "https://api.tuempresa.com/v1/account" \
-H "Authorization: Bearer TU_API_KEY"
```

Si todo está configurado correctamente, deberías recibir una respuesta similar a esta:

```json
jsonCopiar código{
  "id": "12345",
  "name": "John Doe",
  "email": "john.doe@example.com",
  "status": "active"
}
```

#### 4. Explora los Endpoints

Ahora que has realizado tu primera solicitud, explora los demás endpoints disponibles en la sección de Referencias API. Aquí encontrarás detalles sobre cómo acceder a diferentes recursos y realizar operaciones más avanzadas.

#### 5. Soporte

Si encuentras algún problema o tienes preguntas, revisa nuestra sección de preguntas frecuentes o contacta a nuestro equipo de soporte.
