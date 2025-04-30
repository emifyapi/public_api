---
description: >-
  En esta sección tendrás ejemplos de JSON para emitir los diferentes tipos de
  comprobantes.
---

# Argentina

### ¿Cuáles son los tipos de comprobantes a emitir?

Los tipos de factura a emitir por cada venta o locación de servicio, dependerán del sujeto con el que se opere. Para más información, cosultar[ este artículo](https://www.afip.gob.ar/facturacion/regimen-general/comprobantes.asp) de ARCA.

<details>

<summary>Factura A</summary>

```json
{
  "branch_office": 1,
  "invoice_type": "FCA",
  "invoice_date": "2024-07-31 08:00:00",
  "payment_due_date": "2024-07-31",
  "service_start_date": "2024-07-15 00:00:00",
  "service_end_date": "2024-07-30 23:59:59",
  "concept": "3",
  "observations": "Nuestro horario de atención es de Lunes a Sábado de 9 a 20hs",
  "external_reference": "103513046",
  "issuer": {
    "legal_name": "DEMO SRL",
    "document_type": "CUIT",
    "document_number": "20000000000",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "address": "SUIPACHA 250 1",
      "phone": "0810-1566666666"
    },
    "tax_information": null
  },
  "recipient": {
    "legal_name": "LEGAL NAME",
    "document_type": "DNI",
    "document_number": "99999999",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "phone": "123456",
      "address": "ALBERDI 250"
    },
    "tax_information": null
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
      "discount_amount": 0.0,
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
    "sub_total": 13460,
    "discount": 30,
    "taxes": [
      {
          "type": "iva21",
          "amount": 2769.90,
          "base_amount" : 13190.48
      },
      {
          "type": "iva105",
          "amount": 28.35,
          "base_amount" : 270.00
      }
    ],
    "total": 16228.25
  }
}
```

</details>

<details>

<summary>Factura A con Percepciones</summary>

Requisitos:

* Se debe completar global\_taxes con los impuestos necesitados.
* Cada impuesto corresponde con un objeto dentro del array.
* Cada objeto tiene la siguiente estructura:

```
{
    "type": "iva21",
    "base_amount": "1000",
    "amount": "210,
    "rate": "21.00"
}
```

* En donde "type" corresponde con los valores posibles de "code" en Parámetros - Tax Type y "rate" es el valor de la alícuota de Percepción según corresponda.

```
{
  "branch_office": 1,
  "invoice_type": "FCA",
  "invoice_date": "2024-07-31 08:00:00",
  "payment_due_date": "2024-07-31",
  "service_start_date": "2024-07-15 00:00:00",
  "service_end_date": "2024-07-30 23:59:59",
  "concept": "3",
  "observations": "Nuestro horario de atención es de Lunes a Sábado de 9 a 20hs",
  "external_reference": "103513046",
  "global_taxes": [
    {
      "type": "AR_PER_IMP_NAC"
      "base_amount": 13190.48,
      "amount": 395.71,
      "rate": 3.0
    },
    {a
      "type": "AR_PER_IMP_NAC"
      "base_amount": 270.00,
      "amount": 4.05,
      "rate": 1.5
  ]
  "issuer": {
    "legal_name": "DEMO SRL",
    "document_type": "CUIT",
    "document_number": "20000000000",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "address": "SUIPACHA 250 1",
      "phone": "0810-1566666666"
    },
    "tax_information": null
  },
  "recipient": {
    "legal_name": "LEGAL NAME",
    "document_type": "DNI",
    "document_number": "99999999",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "phone": "123456",
      "address": "ALBERDI 250"
    },
    "tax_information": null
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
      "discount_amount": 0.0,
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
    "sub_total": 13460,
    "discount": 30,
    "taxes": [
      {
          "type": "iva21",
          "amount": 2769.90,
          "base_amount" : 13190.48
      },
      {
          "type": "iva105",
          "amount": 28.35,
          "base_amount" : 270.00
      }
    ],
    "total": 16,658.01
  }
}
```

</details>

<details>

<summary>Factura A con IIBB</summary>



Requisitos:

* Se debe completar global\_taxes con los impuestos necesitados.
* Cada impuesto corresponde con un objeto dentro del array.
* Cada objeto tiene la siguiente estructura:

```
{
    "type": "iva21",
    "base_amount": "1000",
    "amount": "210,
    "rate": "21.00"
}
```

* En donde "type" corresponde con los valores posible en Parámetros - Tax Type y "rate" corresponde al type enviado.



</details>

<details>

<summary>Factura B</summary>

```bash
{
  "branch_office": 1,
  "invoice_type": "FCB",
  "invoice_date": "2024-12-17 08:00:00",
  "payment_due_date": "2024-12-17",
  "service_start_date": "2024-12-17 00:00:00",
  "service_end_date": "2024-12-17 23:59:59",
  "concept": "3",
  "observations": "Nuestro horario de atención es de Lunes a Sábado de 9 a 20hs",
  "external_reference": "103513046",
  "issuer": {
    "legal_name": "DEMO SRL",
    "document_type": "CUIT",
    "document_number": "20000000000",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "address": "SUIPACHA 250 1",
      "phone": "0810-1566666666",
    "tax_information": {
      "tax_condition": "RI",
      "start_activities_date": "2020-01-01"
    }
  },
  "recipient": {
    "legal_name": "LEGAL NAME",
    "document_type": "CUIT",
    "document_number": "23123123123",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "phone": "123456",
      "address": "ALBERDI 250"
    },
    "tax_information": {
      "tax_condition": "CF"
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
      "unit_price": 904.06,
      "description": "PHILIPS BODYGROOM BG2024/15",
      "taxes": [
        {
          "type": "AR_IVA_10_5",
          "amount": 94.93,
          "rate": 10.5
        }
      ]
    },
    {
      "quantity": 1,
      "code_unit_of_measure": "u",
      "unit_price": 140.49,
      "discount_amount": 0,
      "description": "Costo de envío",
      "taxes": [
        {
          "type": "AR_IVA_21",
          "amount": 29.50,
          "rate": 21
        }
      ]
    },
    {
      "quantity": 3,
      "code_unit_of_measure": "u",
      "unit_price": 500.00,
      "discount_amount": 0,
      "description": "Producto adicional",
      "taxes": [
        {
          "type": "AR_IVA_21",
          "amount": 315.00,
          "rate": 21
        }
      ]
    }
  ],
  "totals": {
    "sub_total": 2544.55,
    "discount": 0,
    "taxes": [
      {
        "type": "AR_IVA_21",
        "amount": 344.50,
        "base_amount": 1640.49,
        "rate": 21
      },
      {
        "type": "AR_IVA_10_5",
        "amount": 94.93,
        "base_amount": 904.06,
        "rate": 10.5
      }
    ],
    "total": 2983.98
  }

```

</details>

<details>

<summary>Factura C</summary>

```bash
{
  "branch_office": 1,
  "invoice_type": "FCC",
  "invoice_date": "2024-12-17 08:00:00",
  "payment_due_date": "2024-12-17",
  "service_start_date": "2024-12-17 00:00:00",
  "service_end_date": "2024-12-17 23:59:59",
  "concept": "3",
  "observations": "Nuestro horario de atención es de Lunes a Sábado de 9 a 20hs",
  "external_reference": "103513046",
  "issuer": {
    "legal_name": "DEMO SRL",
    "document_type": "CUIT",
    "document_number": "20000000000",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "address": "SUIPACHA 250 1",
      "phone": "0810-1566666666",
    "tax_information": {
      "tax_condition": "MO",
      "start_activities_date": "2020-01-01"
    }
  },
  "recipient": {
    "legal_name": "LEGAL NAME",
    "document_type": "CUIT",
    "document_number": "23123123123",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "phone": "123456",
      "address": "ALBERDI 250"
    },
    "tax_information": {
      "tax_condition": "CF"
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
      "unit_price": 904.06,
      "description": "PHILIPS BODYGROOM BG2024/15",
      "code": {
        "type": "sku",
        "value": "602979944"
      },
      "taxes": [
        {
          "type": "AR_IVA_10_5",
          "amount": 94.93,
          "rate": 10.5
        }
      ]
    },
    {
      "quantity": 1,
      "code_unit_of_measure": "u",
      "unit_price": 140.49,
      "discount_amount": 0,
      "description": "Costo de envío",
      "taxes": [
        {
          "type": "AR_IVA_21",
          "amount": 29.50,
          "rate": 21
        }
      ]
    },
    {
      "quantity": 3,
      "code_unit_of_measure": "u",
      "unit_price": 500.00,
      "discount_amount": 0,
      "description": "Producto adicional",
      "code": {
        "type": "sku",
        "value": "123456789"
      },
      "taxes": [
        {
          "type": "AR_IVA_21",
          "amount": 315.00,
          "rate": 21
        }
      ]
    }
  ],
  "totals": {
    "sub_total": 2544.55,
    "discount": 0,
    "taxes": [
      {
        "type": "AR_IVA_21",
        "amount": 344.50,
        "base_amount": 1640.49,
        "rate": 21
      },
      {
        "type": "AR_IVA_10_5",
        "amount": 94.93,
        "base_amount": 904.06,
        "rate": 10.5
      }
    ],
    "total": 2983.98
  }

```

</details>

<details>

<summary>Factura E</summary>

#### Requisitos:

Completar `additional_export_info`:

#### Ejemplo:

</details>

<details>

<summary>Factura M</summary>

<pre class="language-bash"><code class="lang-bash"><strong>{
</strong>  "branch_office": 1,
  "invoice_type": "FCM",
  "invoice_date": "2024-12-17 08:00:00",
  "payment_due_date": "2024-12-17",
  "service_start_date": "2024-12-17 00:00:00",
  "service_end_date": "2024-12-17 23:59:59",
  "concept": "3",
  "observations": "Nuestro horario de atención es de Lunes a Sábado de 9 a 20hs",
  "external_reference": "103513046",
<strong>  "issuer": {
</strong>    "legal_name": "DEMO SRL",
    "document_type": "CUIT",
    "document_number": "20000000000",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "address": "SUIPACHA 250 1",
      "phone": "0810-1566666666",
    "tax_information": {
      "tax_condition": "RI",
      "start_activities_date": "2020-01-01"
    }
  },
  "recipient": {
    "legal_name": "LEGAL NAME",
    "document_type": "CUIT",
    "document_number": "23123123123",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "phone": "123456",
      "address": "ALBERDI 250"
    },
    "tax_information": {
      "tax_condition": "CF"
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
      "unit_price": 904.06,
      "description": "PHILIPS BODYGROOM BG2024/15",
      "code": {
        "type": "sku",
        "value": "602979944"
      },
      "taxes": [
        {
          "type": "AR_IVA_10_5",
          "amount": 94.93,
          "rate": 10.5
        }
      ]
    },
    {
      "quantity": 1,
      "code_unit_of_measure": "u",
      "unit_price": 140.49,
      "discount_amount": 0,
      "description": "Costo de envío",
      "taxes": [
        {
          "type": "AR_IVA_21",
          "amount": 29.50,
          "rate": 21
        }
      ]
    },
    {
      "quantity": 3,
      "code_unit_of_measure": "u",
      "unit_price": 500.00,
      "discount_amount": 0,
      "description": "Producto adicional",
      "code": {
        "type": "sku",
        "value": "123456789"
      },
      "taxes": [
        {
          "type": "AR_IVA_21",
          "amount": 315.00,
          "rate": 21
        }
      ]
    }
  ],
  "totals": {
    "sub_total": 2544.55,
    "discount": 0,
    "taxes": [
      {
        "type": "AR_IVA_21",
        "amount": 344.50,
        "base_amount": 1640.49,
        "rate": 21
      },
      {
        "type": "AR_IVA_10_5",
        "amount": 94.93,
        "base_amount": 904.06,
        "rate": 10.5
      }
    ],
    "total": 2983.98
  }

</code></pre>

</details>

<details>

<summary>Nota de crédito / débito</summary>

#### Requisitos:

* Tanto para nota de crédito como débito, tendrás que completar la propiedad `billing_reference` con los datos del comprobante a anular:

```json
    "billing_reference": [
        {
            "branch_office": 1,
            "number": 4757,
            "invoice_type": "FCB",
            "invoice_date": "2024-12-17"
        }
    ]
```

* Deberás indicar el `reason_code` a partir de los datos de la [Document Cancellation Reason](../../refencias-api/parametros.md#document-cancellation-reason).

#### Ejemplo:

```bash
{
  "branch_office": 1,
  "invoice_type": "NCB",
  "invoice_date": "2025-01-21",
  "payment_due_date": "2025-02-21",
  "service_start_date": "2025-01-21 00:00:00",
  "service_end_date": "2025-02-21 23:59:59",
  "concept": "3",
  "reason_code": "ANU",
  "observations": "El comprobante se emitio por error",
  "external_reference": "103513046",
  "billing_reference": [
        {
            "branch_office": 1,
            "number": 4757,
            "invoice_type": "FCB",
            "invoice_date": "2024-12-17"
        }
  ],
  "issuer": {
    "legal_name": "DEMO SRL",
    "document_type": "CUIT",
    "document_number": "20000000000",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "address": "SUIPACHA 250 1",
      "phone": "0810-1566666666",
    "tax_information": {
      "tax_condition": "RI",
      "start_activities_date": "2020-01-01"
    }
  },
  "recipient": {
    "legal_name": "LEGAL NAME",
    "document_type": "CUIT",
    "document_number": "23123123123",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "phone": "123456",
      "address": "ALBERDI 250"
    },
    "tax_information": {
      "tax_condition": "CF"
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
      "unit_price": 904.06,
      "description": "PHILIPS BODYGROOM BG2024/15",
      "code": {
        "type": "sku",
        "value": "602979944"
      },
      "taxes": [
        {
          "type": "AR_IVA_10_5",
          "amount": 94.93,
          "rate": 10.5
        }
      ]
    },
    {
      "quantity": 1,
      "code_unit_of_measure": "u",
      "unit_price": 140.49,
      "discount_amount": 0,
      "description": "Costo de envío",
      "taxes": [
        {
          "type": "AR_IVA_21",
          "amount": 29.50,
          "rate": 21
        }
      ]
    },
    {
      "quantity": 3,
      "code_unit_of_measure": "u",
      "unit_price": 500.00,
      "discount_amount": 0,
      "description": "Producto adicional",
      "code": {
        "type": "sku",
        "value": "123456789"
      },
      "taxes": [
        {
          "type": "AR_IVA_21",
          "amount": 315.00,
          "rate": 21
        }
      ]
    }
  ],
  "totals": {
    "sub_total": 2544.55,
    "discount": 0,
    "taxes": [
      {
        "type": "AR_IVA_21",
        "amount": 344.50,
        "base_amount": 1640.49,
        "rate": 21
      },
      {
        "type": "AR_IVA_10_5",
        "amount": 94.93,
        "base_amount": 904.06,
        "rate": 10.5
      }
    ],
    "total": 2983.98
  }
}
```

</details>

<details>

<summary>Factura de crédito electrónica MiPyME</summary>

#### Requisitos:

* Enviar `bank_account` dentro de `additional_header_info` .

Ejemplo:

```bash
{
  "branch_office": 1,
  "invoice_type": "FCYA",
  "invoice_date": "2025-01-21",
  "payment_due_date": "2025-02-21",
  "service_start_date": "2025-01-21 00:00:00",
  "service_end_date": "2025-02-21 23:59:59",
  "concept": "3",
  "observations": "Nuestro horario de atención es de Lunes a Sábado de 9 a 20hs",
  "external_reference": "103513046",
  "additional_header_info": [
  "bank_account": "1238858588899191888344"
  ]
  "issuer": {
    "legal_name": "DEMO SRL",
    "document_type": "CUIT",
    "document_number": "20000000000",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "address": "SUIPACHA 250 1",
      "phone": "0810-1566666666",
    "tax_information": {
      "tax_condition": "RI",
      "start_activities_date": "2020-01-01"
    }
  },
  "recipient": {
    "legal_name": "LEGAL NAME",
    "document_type": "CUIT",
    "document_number": "23123123123",
    "address": {
      "country": "AR",
      "state": "Ciudad de Buenos Aires",
      "phone": "123456",
      "address": "ALBERDI 250"
    },
    "tax_information": {
      "tax_condition": "CF"
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
      "unit_price": 904.06,
      "description": "PHILIPS BODYGROOM BG2024/15",
      "code": {
        "type": "sku",
        "value": "602979944"
      },
      "taxes": [
        {
          "type": "AR_IVA_10_5",
          "amount": 94.93,
          "rate": 10.5
        }
      ]
    },
    {
      "quantity": 1,
      "code_unit_of_measure": "u",
      "unit_price": 140.49,
      "discount_amount": 0,
      "description": "Costo de envío",
      "taxes": [
        {
          "type": "AR_IVA_21",
          "amount": 29.50,
          "rate": 21
        }
      ]
    },
    {
      "quantity": 3,
      "code_unit_of_measure": "u",
      "unit_price": 500.00,
      "discount_amount": 0,
      "description": "Producto adicional",
      "code": {
        "type": "sku",
        "value": "123456789"
      },
      "taxes": [
        {
          "type": "AR_IVA_21",
          "amount": 315.00,
          "rate": 21
        }
      ]
    }
  ],
  "totals": {
    "sub_total": 2544.55,
    "discount": 0,
    "taxes": [
      {
        "type": "AR_IVA_21",
        "amount": 344.50,
        "base_amount": 1640.49,
        "rate": 21
      },
      {
        "type": "AR_IVA_10_5",
        "amount": 94.93,
        "base_amount": 904.06,
        "rate": 10.5
      }
    ],
    "total": 2983.98
  }
}
```

</details>

