---
hidden: true
---

# Errores comunes

#### 🚨 **Errores comunes por recurso**

| Recurso            | Código HTTP | Código de error         | Descripción                                   | Solución recomendada                                   |
| ------------------ | ----------- | ----------------------- | --------------------------------------------- | ------------------------------------------------------ |
| Api Keys           | `400`       | `INVALID_REQUEST`       | Parámetros inválidos o solicitud mal formada. | Verifica los parámetros y el formato de la solicitud.  |
| Api Keys           | `401`       | `UNAUTHORIZED`          | No se proporcionó una API Key válida.         | Incluye una API Key válida en la cabecera `x-api-key`. |
| Certificates       | `404`       | `NOT_FOUND`             | El recurso solicitado no existe.              | Asegúrate de que el `ID` del recurso sea correcto.     |
| Config Enumeration | `500`       | `INTERNAL_SERVER_ERROR` | Error inesperado en el servidor.              | Intenta nuevamente más tarde.                          |
| Config Enumeration | `429`       | `RATE_LIMIT_EXCEEDED`   | Exceso de solicitudes.                        | Espera unos minutos antes de volver a intentar.        |

{% hint style="info" %}
#### 📌 **Nota:** Si recibes un error que no aparece en la tabla o no entiendes la causa, revisa la respuesta del servidor para obtener detalles adicionales o consulta la documentación de [**Errores generales**](https://app.gitbook.com/o/Da7VnFhu7Ry6h1ELpPbo/s/9W4IE71mGDkSPyA8Ym5Z/~/changes/13/como-empezar/errores-generales).
{% endhint %}
