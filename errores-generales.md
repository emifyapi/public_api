# Errores generales

### 📌 **Errores Frecuentes**

Nuestra API devuelve códigos de error estándar para facilitar la identificación y resolución de problemas. A continuación, se detallan los errores más comunes, sus posibles causas y cómo solucionarlos.

#### 🔹 **Formato de Respuesta de Error**

Cuando se produce un error, la API responde con un cuerpo en formato JSON con la siguiente estructura:

```json
jsonCopiarEditar{
  "error": {
    "code": "{codigo_error}",
    "message": "{descripcion_corta}",
    "details": "{informacion_adicional}"
  }
}
```

Donde:

* **`code`** → Código de error específico.
* **`message`** → Descripción breve del error.
* **`details`** → Información adicional sobre la causa del error o posibles soluciones.

***

#### 🔹 **Listado de Errores Comunes**

| Código | Descripción               | Causa                                                        | Solución                                                                               |
| ------ | ------------------------- | ------------------------------------------------------------ | -------------------------------------------------------------------------------------- |
| `400`  | **Bad Request**           | La solicitud tiene parámetros incorrectos o faltantes.       | Verifica que los parámetros enviados sean correctos y cumplan con el formato esperado. |
| `401`  | **Unauthorized**          | No se ha enviado un token de autenticación válido.           | Asegúrate de incluir el token en el encabezado `Authorization`.                        |
| `403`  | **Forbidden**             | El usuario no tiene permisos para acceder al recurso.        | Revisa los permisos de la cuenta o el rol asignado.                                    |
| `404`  | **Not Found**             | El recurso solicitado no existe.                             | Verifica la URL y los identificadores utilizados en la solicitud.                      |
| `409`  | **Conflict**              | Hay un conflicto con el estado actual del recurso.           | Revisa si el recurso ya existe o si hay condiciones que impidan la operación.          |
| `422`  | **Unprocessable Entity**  | La solicitud tiene datos válidos, pero no pueden procesarse. | Valida la estructura y los valores enviados.                                           |
| `429`  | **Too Many Requests**     | Se superó el límite de solicitudes permitido.                | Espera el tiempo indicado en el encabezado `Retry-After` antes de volver a intentar.   |
| `500`  | **Internal Server Error** | Error inesperado en el servidor.                             | Intenta nuevamente más tarde. Si el problema persiste, contacta al soporte.            |
| `503`  | **Service Unavailable**   | El servicio no está disponible temporalmente.                | Reintenta después de unos minutos.                                                     |

***

#### 🔹 **Ejemplo de Respuesta de Error**

```http
httpCopiarEditarHTTP/1.1 400 Bad Request
Content-Type: application/json

{
  "error": {
    "code": "400",
    "message": "Parámetros inválidos",
    "details": "El campo 'email' es obligatorio."
  }
}
```

⚠️ **Nota:** En caso de errores inesperados o problemas con la API, revisa la documentación y los encabezados de la respuesta para obtener más detalles.
