---
hidden: true
---

# Preguntas frencuentes

### 📌 **Preguntas Frecuentes (FAQ)**

A continuación, se responden algunas de las preguntas más comunes sobre el uso de nuestra API.

#### 🔹 **Autenticación y Seguridad**

❓ **¿Cómo me autentico en la API?**\
💬 Para realizar solicitudes, debes incluir un token de autenticación en el encabezado `Authorization`. Ejemplo:

```http
httpCopiarEditarAuthorization: Bearer {tu_token}
```

❓ **¿Cuánto dura el token de autenticación?**\
💬 El token tiene una validez de `{duración}` y debe renovarse antes de su vencimiento.

❓ **¿Cómo renuevo mi token de acceso?**\
💬 Puedes solicitar un nuevo token enviando una solicitud al endpoint `{endpoint_de_auth}` con tus credenciales.

***

#### 🔹 **Rate Limit y Uso de la API**

❓ **¿Cuántas solicitudes puedo hacer por minuto?**\
💬 La API permite `{cantidad}` solicitudes por `{periodo}`. Si superas este límite, recibirás un error `429 Too Many Requests`.

❓ **¿Cómo sé cuántas solicitudes me quedan?**\
💬 En cada respuesta de la API, incluimos encabezados como `X-Rate-Limit-Remaining` para indicar el número de solicitudes restantes.

***

#### 🔹 **Paginado y Manejo de Datos**

❓ **¿Cómo funciona la paginación en la API?**\
💬 Nuestra API utiliza `{tipo_de_paginado}`. Debes incluir los parámetros `{parametro_offset}` y `{parametro_limit}` en la URL.

Ejemplo:

```http
/recurso?{parametro_offset}=XX&{parametro_limit}=XX
```

❓ **¿Cómo obtengo la siguiente página de resultados?**\
💬 En la respuesta, encontrarás la clave `"next"` con la URL de la siguiente página.

***

#### 🔹 **Errores y Solución de Problemas**

❓ **¿Qué hago si recibo un error 400 Bad Request?**\
💬 Revisa los parámetros de la solicitud. Asegúrate de que sean correctos y cumplan con el formato esperado.

❓ **¿Por qué obtengo un error 401 Unauthorized?**\
💬 Puede ser que el token de autenticación sea inválido o haya expirado. Verifica tu token y renueva si es necesario.

❓ **¿Qué significa el error 500 Internal Server Error?**\
💬 Es un error en nuestros servidores. Intenta nuevamente más tarde y, si persiste, contáctanos.

***

#### 🔹 **Soporte y Contacto**

❓ **¿Dónde puedo reportar un problema con la API?**\
💬 Puedes reportar incidencias a través de `{correo_de_soporte}` o en `{plataforma_de_soporte}`.

❓ **¿Existe un ambiente de pruebas (sandbox)?**\
💬 Sí, ofrecemos un entorno de pruebas en `{URL_sandbox}`, donde puedes simular solicitudes sin afectar datos reales.
