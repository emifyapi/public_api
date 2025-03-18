# Webhooks

Los webhooks permiten recibir notificaciones en tiempo real cuando ocurren eventos específicos en nuestra plataforma. En lugar de realizar consultas periódicas (polling) para verificar cambios, puedes configurar un webhook para que nuestra API envíe automáticamente una notificación a tu servidor cuando se produzca un evento relevante.

### **Funcionamiento**

1. **Registro del Webhook**: Debes proporcionar una URL a la que enviaremos las notificaciones.
2. **Evento Disparador**: Cuando ocurre un evento configurado, nuestro sistema envía una solicitud HTTP `POST` a tu endpoint.
3. **Formato del Payload**: La información del evento se envía en formato JSON en el cuerpo de la solicitud.
4. **Respuesta Esperada**: Tu servidor debe responder dentro de los primeros 5 segundos con un código HTTP `200` para confirmar la recepción. Para más información sobre reintentos, ver sección [**Manejo de Respuestas**](webhooks.md#manejo-de-respuestas)**.**

### **Eventos Disponibles**

Se pueden consultar los eventos disponibles a través del siguiente recurso:

```bash
curl --location '{{base_url}}/api/companies/webhooks/events' \
--header 'x-api-key: {{apiKey}}'
```

#### Lista de eventos:

<table><thead><tr><th width="178">Evento</th><th>Descripción</th><th data-hidden></th></tr></thead><tbody><tr><td>ISE</td><td>Notificación sobre cambios en el estado de un comprobante electrónico.</td><td></td></tr><tr><td>REC</td><td>Aviso de recepción de un comprobante de compra.</td><td></td></tr><tr><td>CER</td><td>Notificación sobre el próximo vencimiento de un certificado digital.</td><td></td></tr><tr><td>ENU</td><td>Alerta sobre el vencimiento o la baja disponibilidad de enumeraciones en el sistema (Folios en Chile y CAEs en Uruguay).</td><td></td></tr></tbody></table>

### **Configuración**

Para registrar un webhook, realiza una solicitud `POST` a nuestro endpoint de configuración con los siguientes parámetros:

**Solicitud**

```http
POST /api/companies/{{id_company}}/webhooks
Content-Type: application/json

{
    "url" : "https://callback.emify.com",
    "events" : ["ISE",  "CER"],
    "description" : "description test"
}
```

{% hint style="warning" %}
Solo se puede configurar una URL Callback por empresa con la cantidad de eventos que necesites.
{% endhint %}

**Respuesta Exitosa**

```json
{
    "id": 2,
    "url": "https://callback.emify.com",
    "description": "description test",
    "events": [ "ISE", "CER" ],
    "status": "active"
}
```

#### Respuesta con error

```json
{
    "code": "Webhook suscription already exists",
    "message": "WEBHOOK_SUSCRIPTION_ALREADY_EXISTS"
}
```

**Ejemplo de Notificación Recibida para evento ISE**

Cuando ocurra un evento, enviaremos un `POST` con el siguiente formato:

```json
{
    "document_id": "",
    "event": "Manejo de Respuestas",
    "external_reference": "",
    "status": "Accepted",
    "authorization_type": "CAE",
    "authorization_code": "75100224356849",
    "authorization_expiration_date": "18/03/2022 12:05:00",
    "authorization_qr": "https://www.afip.gob.ar/fe/qr/?p=eyJ2ZXIiO...",
    "error_message": "",
    "attempt":1,
    "created_at":""
  }
```

#### **Manejo de Respuestas**

* **Éxito (`200`)**: Confirmamos que el webhook fue recibido correctamente.
* **Cualquier otra respuesta**: Intentaremos reenviar la notificación hasta un máximo de 5 intentos con intervalos crecientes hasta obtener un `Éxito (200)`:

<table><thead><tr><th>Intento</th><th>Intervalo [segundos]</th><th data-hidden></th></tr></thead><tbody><tr><td>Primero</td><td>5</td><td></td></tr><tr><td>Segundo</td><td>60</td><td></td></tr><tr><td>Tercero</td><td>300 = 5 min</td><td></td></tr><tr><td>Cuarto</td><td>1200 = 20 min</td><td></td></tr><tr><td>Quinto</td><td>3600 = 1 h</td><td></td></tr></tbody></table>

#### **Seguridad**

Para garantizar la autenticidad de los webhooks:

* Nuestra IP es ---—  la cual recomendamos agregar en una whitelist en tu servidor para evitar bloqueos.
* Se recomienda validar la procedencia de los eventos antes de procesarlos.

#### **Mejores Prácticas**

✔ Responder rápidamente con un código `200 OK`.\
✔ Usar colas de procesamiento en segundo plano.\
✔ Validar el origen del webhook antes de procesarlo.
