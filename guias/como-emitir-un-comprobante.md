---
hidden: true
---

# Cómo emitir un comprobante

Esta guía de inicio rápido te permitirá emitir un comprobante en donde se incluye la creación, consulta de estado, ejemplos de cada tipo de comprobante y su impresión. Para el conjunto de estos endpoints en necesario usar la API Key de tu empresa en cada petición. A continuación, te llevaremos paso a paso:

{% hint style="warning" %}
Tu API Key se genera al momento de crear tu empresa y deberás tenerla guardada en lugar seguro dado que no podrás consultarla en otro momento.
{% endhint %}

#### 1. Envía una petición POST:

Utiliza el siguiente comando `curl` para enviar una solicitud POST a la API y emitir el comprobante:

{% hint style="warning" %}
Asegúrate de reemplazar `{{apiKey}}` con tu clave de API válida.
{% endhint %}

<details>

<summary>Request POST invoice</summary>

```bash
curl --POST --location '{{base_url}}/api/invoices' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {{apiKey}}' \
--data '{
  "branch_office": 1,
  "invoice_type": "FCA",
  "invoice_date": "2024-10-24 08:00:00",
  "payment_due_date": "2024-10-24",
  "service_start_date": "2024-10-24 00:00:00",
  "service_end_date": "2024-10-24 23:59:59",
  "concept": "3",
  "observations": "Nuestro horario de atención es de Lunes a Sábado de 9 a 20hs",
  "external_reference": "103513046",
  "issuer": {
    "legal_name": "issuer name",
    "document_type": "CUIT",
    "document_number": "20000000000",
    "address": {
      "country": "AR",
      "region": "AR-C",
      "address": "direccion issuer",
      "phone": "1155555555"
    }
  },
  "recipient": {
    "legal_name": "recipient name",
    "document_type": "CUIT",
    "document_number": "20555555555",
    "address": {
      "country": "AR",
      "region": "AR-C",
      "phone": "123456",
      "address" : "direccion recipient"
    }
  },
  "currency": {
    "code": "ARS",
    "exchange_rate": 1
  },
  "payment_method": {
    "code": "CON",
    "description": "Cuenta corriente"
  },
  "items": [
    {
      "quantity": 1,
      "code_unit_of_measure": "u",
      "discount_amount": 0,
      "unit_price": 95,
      "description": "A PRODUCTO",
      "code": {
        "type": "sku",
        "value": "898765"
      },
      "taxes": [
        {
            "type": "iva21",
            "amount": 19.95,
            "rate": 21
        }
      ]
    },
    {
      "quantity": 3,
      "code_unit_of_measure": "u",
      "unit_price": 100,
      "discount_amount": 10,
      "description": "prod b ",
      "taxes": [
        {
            "type": "iva105",
            "amount": 9.45,
            "rate": 10.50
        }
      ]
    },
    {
      "quantity": 1,
      "code_unit_of_measure": "u",
      "unit_price": 13000,
      "discount_amount": 0,
      "description": "1HSCONSUL",
      "code": {
        "type": "sku",
        "value": "1HSCONSUL"
      },
      "taxes": [
        {
            "type": "iva21",
            "amount": 2730,
            "rate": 21
        }
      ]
    }
  ],
  "totals": {
    "sub_total": 13395,
    "discount": 30,
    "taxes": [
      {
          "type": "iva21",
          "amount": 2749.95,
          "base_amount" : 13095
      },
      {
          "type": "iva105",
          "amount": 28.35,
          "base_amount" : 270.00
      }
    ],
    "total": 16143.30
  }
}'
```

</details>

Este paso configura la información del comprobante, incluyendo el emisor, el destinatario, los productos o servicios, y los impuestos.

#### 2. Consulta el comprobante emitido

Luego de emitir el comprobante, podrás consultar su estado ante el organismo fiscal y demás información auto generada a través de la siguiente petición:

<pre class="language-bash"><code class="lang-bash">curl --GET --location '{{base_url}}/api/invoices/{{invoice_id}}' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {{apiKey}}' \
<strong>--header 'Accept: application/json'
</strong>
</code></pre>

En donde la respuesta es la siguiente:

<details>

<summary>Response GET invoice</summary>

```bash
{
    "id": "66fe933c58e4ac7a85010262",
    "branch_office": 1,
    "number": "0001-00012345",
    "invoice_type": "FCA",
    "invoice_date": "2024-10-24",
    "payment_due_date": "2024-10-24",
    "service_start_date": "2024-10-24 00:00:00",
    "service_end_date": "2024-10-24 23:59:59",
    "concept": "3",
    "reason_code": null,
    "cancellation_date": null,
    "observations": "Nuestro horario de atención es de Lunes a Sábado de 9 a 20hs",
    "external_reference": "103513046",
    "status": "Approved",
    "issuer": {
        "legal_name": "issuer name",
        "document_type": "CUIT",
        "document_number": "20000000000",
        "address": {
          "country": "AR",
          "region": "AR-C",
          "address": "direccion issuer",
          "phone": "1155555555"
      }
      },
   "recipient": {
        "legal_name": "recipient name",
        "document_type": "CUIT",
        "document_number": "20555555555",
        "address": {
            "country": "AR",
            "region": "AR-C",
            "phone": "123456",
            "address" : "direccion recipient"
            }
        },
        "tax_information": null
    },
    "currency": {
        "code": "ARS",
        "exchange_rate": 1
    },
    "items": [
        {
            "quantity": 1,
            "code_unit_of_measure": "u",
            "unit_price": 95,
            "description": "A PRODUCTO",
            "code": {
                "type": "sku",
                "value": "898765"
            },
            "taxes": [
                {
                    "type": "iva21",
                    "amount": 19.95,
                    "rate": 21
                }
            ],
            "type_organization_code": "5",
            "code_unit_of_measure_organization_code": "7",
            "discount_amount": 0
        },
        {
            "quantity": 3,
            "code_unit_of_measure": "u",
            "unit_price": 100,
            "description": "prod b",
            "taxes": [
                {
                    "type": "iva105",
                    "amount": 9.45,
                    "rate": 10.5
                }
            ],
            "type_organization_code": "4",
            "code_unit_of_measure_organization_code": "7",
            "discount_amount": 10
        },
        {
            "quantity": 1,
            "code_unit_of_measure": "u",
            "unit_price": 13000,
            "description": "1HSCONSUL",
            "code": {
                "type": "sku",
                "value": "1HSCONSUL"
            },
            "taxes": [
                {
                    "type": "iva21",
                    "amount": 2730,
                    "rate": 21
                }
            ],
            "type_organization_code": "5",
            "code_unit_of_measure_organization_code": "7",
            "discount_amount": 0
        }
    ],
    "global_taxes": [],
    "totals": {
        "sub_total": 13395,
        "discount": 30,
        "total": 16143.3,
        "taxes": [
            {
                "type": "iva21",
                "base_amount": 13095,
                "amount": 2749.95
            },
            {
                "type": "iva105",
                "base_amount": 270,
                "amount": 28.35
            }
        ]
    },
    "additional_header_info": null,
    "additional_export_info": null,
    "electronic_authorization": {
        "type": "CAE",
        "code": "61123000000001",
        "expiration_date": "2024-10-31",
        "qr": "https://www.afip.gob.ar/qr/?p=...",
        "additional_info": null
    },
    "billing_reference": []
}
```

</details>

Una vez recibida la respuesta de la consulta del comprobante, puedes interpretar sus diversos campos para obtener información relevante. Aquí te explicamos algunos de los elementos principales:

* **`id`**: Identificador único del comprobante en el sistema. Se genera automáticamente al momento de la creación y permite consultar el comprobante específico.
* **`number`**: Representa el número único del comprobante emitido (e.g., "0001-00012345"). En el POST no se proporciona, ya que se asigna después de la emisión y se utiliza en el GET para identificar la factura emitida.
* **`status`**: Indica el estado actual del comprobante, como "Pending" (pendiente) o "Accepted" (Aceptado). El estado inicial suele ser "Pending" hasta el procesamiento del comprobante, lo que puede suceder automáticamente o requerir intervención. Los distintos estados son los siguientes:



<figure><img src="../.gitbook/assets/estados (1).png" alt=""><figcaption><p>Transición de estados de un comprobante</p></figcaption></figure>

{% hint style="info" %}
* "Pending": el comprobante está pendiente por ser procesado.
* "In process": el comprobante se encuentra esperando respuesta del ente fiscal.
* "Accepted": el comprobante se encuentra aceptado y exitosamente emitido al ente fiscal.
* "Rejected": el comprobante se encuentra rechazado. Ver motivo.
{% endhint %}

* **`electronic_authorization`**: Contiene datos de autorización electrónica en caso de estar en estado "Accepted", como el tipo (e.g., "CAE"), el código de autorización asignado (en este caso, "61123000000001"), la fecha de expiración, y un enlace a un código QR. Esta información no se incluye en el POST inicial, ya que se genera tras la emisión del comprobante y se recupera en el GET.

Con esta información, puedes verificar la validez del comprobante y gestionar los procesos administrativos relacionados.

3. Consultar estado del comprobante

#### 3. Obtén el PDF del comprobante

Una vez que `status` del comprobante sea `accepted`, podrás obtener el comprobante en A4 con la siguiente petición:

```bash
curl --location --request POST '{{base_url}}/api/invoices/{{invoice_id}}/download-pdf/A4' \
--header 'x-api-key: {{apiKey}}'
```

Respuesta:

<figure><img src="../.gitbook/assets/descarga.png" alt=""><figcaption></figcaption></figure>

Para otras medidas, consultar las [referencias de Emisión e Impresión](../refencias-api/emision-e-impresion.md).

