# Preguntas frencuentes

### 📌 **Preguntas Frecuentes (FAQ)**

A continuación, se responden algunas de las preguntas más comunes sobre el uso de nuestra API.

#### 🔹 **Autenticación y Seguridad**

❓ **¿Cómo me autentico en la API?**\
💬 Para realizar solicitudes, debes incluir un token de autenticación en el encabezado `Authorization`. Ejemplo:

```http
Authorization: Bearer {tu_token}
```

❓ **¿Cuánto dura el token de autenticación?**\
💬 El token tiene una validez de `{24 horas}` y debe renovarse antes de su vencimiento.

❓ **¿Cómo renuevo mi token de acceso?**\
💬 Puedes solicitar un nuevo token enviando una solicitud al endpoint `{/login}` con tus credenciales.

***

#### 🔹 **Rate Limit y Uso de la API**

❓ **¿Cuántas solicitudes puedo hacer por minuto?**\
💬 La API permite `{`50`}` solicitudes por `{segundo}`. Si superas este límite, recibirás un error `429 Too Many Requests`.

❓ **¿Cómo sé cuántas solicitudes me quedan?**\
💬 En cada respuesta de la API, incluimos encabezados como `X-Rate-Limit-Remaining` para indicar el número de solicitudes restantes.

***

#### 🔹 **Errores y Solución de Problemas**

❓ **¿Qué hago si recibo un error 400 Bad Request?**\
💬 Revisa los parámetros de la solicitud. Asegúrate de que sean correctos y cumplan con el formato esperado.

❓ **¿Por qué obtengo un error 401 Unauthorized?**\
💬 Puede ser que el token de autenticación sea inválido o haya expirado. Verifica tu token y renueva si es necesario.

❓ **¿Qué significa el error 500 Internal Server Error?**\
💬 Es un error en nuestros servidores. Intenta nuevamente más tarde y, si persiste, contáctanos.

***

❓ **¿Existe un ambiente de pruebas (sandbox)?**\
💬 Sí, ofrecemos un entorno de pruebas en `https://sandbox.emify.co/`, donde puedes simular solicitudes sin afectar datos reales.
