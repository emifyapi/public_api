# Webhooks

Los webhooks permiten recibir notificaciones en tiempo real cuando ocurren eventos específicos en nuestra plataforma. En lugar de realizar consultas periódicas (polling) para verificar cambios, puedes configurar un webhook para que nuestra API envíe automáticamente una notificación a tu servidor cuando se produzca un evento relevante.

### **Funcionamiento**

1. **Registro del Webhook**: Debes proporcionar una URL a la que enviaremos las notificaciones.
2. **Evento Disparador**: Cuando ocurre un evento configurado, nuestro sistema envía una solicitud HTTP `POST` a tu endpoint.
3. **Formato del Payload**: La información del evento se envía en formato JSON en el cuerpo de la solicitud.
4. **Respuesta Esperada**: Tu servidor debe responder dentro de los primeros 1000 ms con un código HTTP `200` para confirmar la recepción. Para más información sobre reintentos, ver sección [**Manejo de Respuestas**](webhooks.md#manejo-de-respuestas)**.**

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

### **Ejemplo de Notificación Recibida para evento ISE**

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

### **Ejemplo de Notificación Recibida para evento REC**

Cuando ocurra un evento REC, enviaremos un `POST` con el siguiente formato:

####

### **Ejemplo de Notificación Recibida para evento CER**

Cuando ocurra un evento CER, enviaremos un `POST` con el siguiente formato:

```
```

#### **Frecuencia de Avisos de Vencimiento de Certificado**

| **Días antes del vencimiento** | **Descripción del Aviso**                        |
| ------------------------------ | ------------------------------------------------ |
| 60 días                        | Primera alerta de vencimiento próximo.           |
| 45 días                        | Segunda alerta de vencimiento próximo.           |
| 30 días                        | Tercera alerta de vencimiento próximo.           |
| 15 días                        | Cuarta alerta de vencimiento próximo.            |
| 5 días                         | Quinta alerta, el vencimiento es inminente.      |
| 2 días                         | Sexta alerta, quedan solo 48 horas.              |
| 1 día                          | Última alerta, el certificado vence en 24 horas. |

### **Ejemplo de Notificación Recibida para evento ENU**

Cuando ocurra un evento **ENU**, enviaremos un `POST` con el siguiente formato:

```
```

#### **Frecuencia de Avisos por Cantidad Restante**

| **Tipo de Documento**      | **Primer Aviso** (Cantidad Baja) | **Segundo Aviso** (1 Unidad Restante) | **Tercer Aviso** (Sin Folios) |
| -------------------------- | -------------------------------- | ------------------------------------- | ----------------------------- |
| **Boletas**                | ≤ 50 folios o 20% del total      | 1 folio restante                      | 0 folios disponibles          |
| **Facturas / Exportación** | ≤ 20 folios o 20% del total      | 1 folio restante                      | 0 folios disponibles          |
| **Notas de Crédito**       | ≤ 10 folios o 20% del total      | 1 folio restante                      | 0 folios disponibles          |
| **Notas de Débito**        | ≤ 10 folios o 20% del total      | 1 folio restante                      | 0 folios disponibles          |
| **Guías de Despacho**      | ≤ 10 folios o 20% del total      | 1 folio restante                      | 0 folios disponibles          |

#### **Frecuencia de Avisos por Fecha de Vencimiento**

| **Días antes/después del vencimiento** | **Descripción del Aviso**               |
| -------------------------------------- | --------------------------------------- |
| 7 días antes                           | Primer aviso de vencimiento próximo.    |
| 1 día antes                            | Segundo aviso de vencimiento inminente. |
| El día del vencimiento                 | Tercer aviso: los folios vencen hoy.    |
| 1 día después                          | Cuarto aviso: los folios han vencido.   |

#### **Manejo de Respuestas**

* **Éxito (`200`)**: Confirma que el webhook fue recibido correctamente dentro de los 1000 ms luego de recibida la notificación.
* **Cualquier otra respuesta**: Intentaremos reenviar la notificación hasta un máximo de 11 intentos con intervalos crecientes hasta obtener un `Éxito (200)`:

<table><thead><tr><th>Intento</th><th>Intervalo</th><th data-type="number">Tiempo de respuesta [ms]</th><th data-hidden></th></tr></thead><tbody><tr><td>Primero</td><td>5 s</td><td>1000</td><td></td></tr><tr><td>Segundo</td><td>60 s</td><td>1000</td><td></td></tr><tr><td>Tercero</td><td>300 s = 5 min</td><td>1000</td><td></td></tr><tr><td>Cuarto</td><td>1200 s = 20 min</td><td>1000</td><td></td></tr><tr><td>Quinto</td><td>3600 s = 1 h</td><td>1000</td><td></td></tr><tr><td>Sexto</td><td>24 h</td><td>1000</td><td></td></tr><tr><td>Séptimo</td><td>24 h</td><td>1000</td><td></td></tr><tr><td>Octavo</td><td>24 h</td><td>1000</td><td></td></tr><tr><td>Noveno</td><td>24 h</td><td>1000</td><td></td></tr><tr><td>Décimo</td><td>24 h</td><td>1000</td><td></td></tr></tbody></table>

#### **Seguridad**

Para garantizar la autenticidad de los webhooks:

* Nuestra IP es ---—  la cual recomendamos agregar en una whitelist en tu servidor para evitar bloqueos.
* Se recomienda validar la procedencia de los eventos antes de procesarlos.

#### **Mejores Prácticas**

✔ Responder rápidamente con un código `200 OK`.\
✔ Usar colas de procesamiento en segundo plano.\
✔ Validar el origen del webhook antes de procesarlo.
