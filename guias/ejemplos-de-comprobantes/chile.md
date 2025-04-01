---
description: Agrupar por facturas y boletas
---

# Chile

<details>

<summary>Factura Electrónica</summary>

```bash
{
   "branch_office": 1,
   "invoice_type": "FCE",
   "invoice_date": "2025-01-31 06:00:00",
   "payment_due_date": "2025-01-31",
   "external_reference": "1526815",
   "issuer": {
       "legal_name": "CONTABILIUM CHILE SPA",
       "document_type": "RUT",
       "document_number": "77450199-1",
       "address": {
           "country": "CL",
           "region": "CL-AN",
           "city": "CL-ANF",
           "address": "Napoleon 3200"
       },
       "tax_information": {
           "activity": "OTRAS ACTIVIDADES DE TECNOLOGIA DE LA INFORMACION Y DE SERVICIOS INFORMATICOS",
           "activity_codes": [
               620200,
               620900,
               702000
           ],
           "resolution_date": "2014-08-22",
           "resolution_number": "80"
       }
   },
   "recipient": {
       "legal_name": "TUDISTRIBUIDORA.CL SPA",
       "document_type": "RUT",
       "document_number": "76995025-7",
       "address": {
           "country": "CL",
           "region": "CL-LI",
           "city": "CL-QTC",
           "address": "LOS MILITARES 5620 OF 905"
       },
       "tax_information": {
           "activity": "VENTAS DE PRODUCTOS"
       }
   },
   "currency": {
       "code": "CLP",
       "exchange_rate": 1
   },
   "payment_method": {
       "code": "CON",
       "description": "Contado"
   },
   "export_payment_method": {
       "code": "CH1"
   },
   "items": [
       {
           "quantity": 2,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 5,
           "description": "PLAN FULL",
           "taxes": [
               {
                   "type": "CL_GRAV_BAS",
                   "amount": 2,
                   "rate": 19
               }
           ]
       },
       {
           "quantity": 1,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 7,
           "description": "INSTALACION SET BASICO",
           "taxes": [
               {
                   "type": "CL_GRAV_BAS",
                   "amount": 1,
                   "rate": 19
               }
           ]
       }
   ],
   "totals": {
       "sub_total": 17,
       "discount": 0,
       "taxes": [
           {
               "type": "CL_GRAV_BAS",
               "amount": 3,
               "base_amount": 17,
               "rate": 19
           }
       ],
       "total": 20
   }
}

```

</details>

<details>

<summary>Factura Electrónica No afectos o Exentos</summary>

```
{
   "branch_office": 1,
   "invoice_type": "FCEE",
   "invoice_date": "2025-01-31 06:00:00",
   "payment_due_date": "2025-01-31",
   "external_reference": "1526815",
   "issuer": {
       "legal_name": "CONTABILIUM CHILE SPA",
       "document_type": "RUT",
       "document_number": "77450199-1",
       "address": {
           "country": "CL",
           "region": "CL-AN",
           "city": "CL-ANF",
           "address": "Napoleon 3200"
       },
       "tax_information": {
           "activity": "OTRAS ACTIVIDADES DE TECNOLOGIA DE LA INFORMACION Y DE SERVICIOS INFORMATICOS",
           "activity_codes": [
               620200,
               620900,
               702000
           ],
           "resolution_date": "2014-08-22",
           "resolution_number": "80"
       }
   },
   "recipient": {
       "legal_name": "TUDISTRIBUIDORA.CL SPA",
       "document_type": "RUT",
       "document_number": "76995025-7",
       "address": {
           "country": "CL",
           "region": "CL-LI",
           "city": "CL-QTC",
           "address": "LOS MILITARES 5620 OF 905"
       },
       "tax_information": {
           "activity": "VENTAS DE PRODUCTOS"
       }
   },
   "currency": {
       "code": "CLP",
       "exchange_rate": 1
   },
   "payment_method": {
       "code": "CON",
       "description": "Contado"
   },
   "export_payment_method": {
       "code": "CH1"
   },
   "items": [
       {
           "quantity": 2,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 5,
           "description": "PLAN FULL",
           "taxes": [
               {
                   "type": "CL_EX_IVA",
                   "amount": 0,
                   "rate": 0
               }
           ]
       },
       {
           "quantity": 1,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 7,
           "description": "INSTALACION SET BASICO",
           "taxes": [
               {
                   "type": "CL_EX_IVA",
                   "amount": 0,
                   "rate": 0
               }
           ]
       }
   ],
   "totals": {
       "sub_total": 17,
       "discount": 0,
       "taxes": [
           {
               "type": "CL_EX_IVA",
               "amount": 0,
               "base_amount": 17,
               "rate": 0
           }
       ],
       "total": 17
   }
}

```

</details>

<details>

<summary>Factura de exportación</summary>



</details>

<details>

<summary>Nota de Débito Electrónica</summary>

```bash
{
   "branch_office": 1,
   "invoice_type": "NDV",
   "cancellation_date":"2025-01-30"
   "invoice_date": "2025-01-30 16:00:00",
   "payment_due_date": "2025-01-30",
   "external_reference": "1515",
   "issuer": {
       "legal_name": "CONTABILIUM CHILE SPA",
       "document_type": "RUT",
       "document_number": "77450199-1",
       "address": {
           "country": "CL",
           "region": "CL-RM",
           "city": "CL-LC",
           "address": "Napoleon 3200"
       },
       "tax_information": {
           "activity": "OTRAS ACTIVIDADES DE TECNOLOGIA DE LA INFORMACION Y DE SERVICIOS INFORMATICOS",
           "activity_codes": [
               620200,
               620900,
               702000
           ],
           "resolution_date": "2014-08-22",
           "resolution_number": "80"
       }
   },
   "recipient": {
       "legal_name": "CONSUMIDOR FINAL",
       "document_type": "RUT",
       "document_number": "66666666-6",
       "address": {
           "country": "CL",
           "address": "sin direccion"
       },
       "tax_information": {
           "activity": "sin giro"
       }
   },
   "reason_code":"ANU",
   "billing_reference": [
       {
           "branch_office": 1,
           "number": 65,
           "invoice_type": "BOL",
           "invoice_date": "2025-01-30 16:00:00"
       }
   ],
   "currency": {
       "code": "CLP",
       "exchange_rate": 1
   },
   "payment_method": {
       "code": "CON",
       "description": "Contado"
   },
   "items": [
       {
           "quantity": 2,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 5,
           "description": "PLAN FULL",
           "taxes": [
               {
                   "type": "CL_GRAV_BAS",
                   "amount": 2,
                   "rate": 19
               }
           ]
       },
       {
           "quantity": 1,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 7,
           "description": "INSTALACION SET BASICO",
           "taxes": [
               {
                   "type": "CL_GRAV_BAS",
                   "amount": 1,
                   "rate": 19
               }
           ]
       }
   ],
   "totals": {
       "sub_total": 17,
       "discount": 0,
       "taxes": [
           {
               "type": "CL_GRAV_BAS",
               "amount": 3,
               "base_amount": 17,
               "rate": 19
           }
       ],
       "total": 20
   }
}

```

</details>

<details>

<summary>Nota de Crédito Electrónica</summary>

```bash
{
   "branch_office": 1,
   "invoice_type": "NCV",
   "cancellation_date":"2025-01-30"
   "invoice_date": "2025-01-30 16:00:00",
   "payment_due_date": "2025-01-30",
   "external_reference": "1515",
   "issuer": {
       "legal_name": "CONTABILIUM CHILE SPA",
       "document_type": "RUT",
       "document_number": "77450199-1",
      "address": {
           "country": "CL",
           "region": "CL-AN",
           "city": "CL-ANF",
           "address": "Napoleon 3200"
       },
       "tax_information": {
           "activity": "OTRAS ACTIVIDADES DE TECNOLOGIA DE LA INFORMACION Y DE SERVICIOS INFORMATICOS",
           "activity_codes": [
               620200,
               620900,
               702000
           ],
           "resolution_date": "2014-08-22",
           "resolution_number": "80"
       }
   },
   "recipient": {
       "legal_name": "CONSUMIDOR FINAL",
       "document_type": "RUT",
       "document_number": "66666666-6",
       "address": {
           "country": "CL",
           "address": "sin direccion"
       },
       "tax_information": {
           "activity": "sin giro"
       }
   },
   "reason_code":"ANU",
   "billing_reference": [
       {
           "branch_office": 1,
           "number": 65,
           "invoice_type": "BOL",
           "invoice_date": "2025-01-30 16:00:00",
       }
   ],
   "currency": {
       "code": "CLP",
       "exchange_rate": 1
   },
   "payment_method": {
       "code": "CON",
       "description": "Contado"
   },
   "items": [
       {
           "quantity": 2,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 5,
           "description": "PLAN FULL",
           "taxes": [
               {
                   "type": "CL_GRAV_BAS",
                   "amount": 2,
                   "rate": 19
               }
           ]
       },
       {
           "quantity": 1,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 7,
           "description": "INSTALACION SET BASICO",
           "taxes": [
               {
                   "type": "CL_GRAV_BAS",
                   "amount": 1,
                   "rate": 19
               }
           ]
       }
   ],
   "totals": {
       "sub_total": 17,
       "discount": 0,
       "taxes": [
           {
               "type": "CL_GRAV_BAS",
               "amount": 3,
               "base_amount": 17,
               "rate": 19
           }
       ],
       "total": 20
   }
}

```

</details>

<details>

<summary>Guía de Despacho Electrónica</summary>

```bash
{
   "branch_office": 1,
   "invoice_type": "GDE",
   "invoice_date": "2025-01-30 16:00:00",
   "payment_due_date": "2025-01-30",
   "external_reference": "1515",
   "issuer": {
       "legal_name": "CONTABILIUM CHILE SPA",
       "document_type": "RUT",
       "document_number": "77450199-1",
       "address": {
           "country": "CL",
           "region": "CL-RM",
           "city": "CL-LC",
           "address": "Napoleon 3200"
       },
       "tax_information": {
           "activity": "OTRAS ACTIVIDADES DE TECNOLOGIA DE LA INFORMACION Y DE SERVICIOS INFORMATICOS",
           "activity_codes": [
               620200,
               620900,
               702000
           ],
           "resolution_date": "2014-08-22",
           "resolution_number": "80"
       }
   },
   "recipient": {
       "legal_name": "TUDISTRIBUIDORA.CL SPA",
       "document_type": "RUT",
       "document_number": "76995025-7",
       "address": {
           "country": "CL",
           "region": "CL-RM",
           "city": "CL-LC",
           "address": "LOS MILITARES 5620 OF 905"
       },
       "tax_information": {
           "activity": "VENTAS DE PRODUCTOS"
       }
   },
   "additional_header_info": {
       "transfer_type": "VPE",
       "dispatch_type": "DCR",
       "transport": {
           "license_plate": "ABC123",
           "rut_transport": "11371390-9",
           "driver": {
               "rut": "11371390-9",
               "name": "WILMAR FUENZALIDA"
           },
           "destination_city": "Region Metropolitana",
           "destination_region": "LAS CONDES",
           "destination_address": "LOS MILITARES 5620"
       }
   },
   "currency": {
       "code": "CLP",
       "exchange_rate": 1
   },
   "payment_method": {
       "code": "CON",
       "description": "Contado"
   },
   "items": [
       {
           "quantity": 1,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 8,
           "description": "Resma de papel tamaño carta",
           "taxes": [
               {
                   "type": "CL_GRAV_BAS",
                   "amount": 2,
                   "rate": 19
               }
           ]
       }
   ],
   "totals": {
       "sub_total": 8,
       "discount": 0,
       "taxes": [
           {
               "type": "CL_GRAV_BAS",
               "amount": 2,
               "base_amount": 8,
               "rate": 19
           }
       ],
       "total": 10
   }
}

```

</details>

<details>

<summary>Boleta Electrónica</summary>

```bash
{
   "branch_office": 1,
   "invoice_type": "BOL",
   "invoice_date": "2025-01-30 16:00:00",
   "payment_due_date": "2025-01-30",
   "external_reference": "1515",
   "issuer": {
       "legal_name": "CONTABILIUM CHILE SPA",
       "document_type": "RUT",
       "document_number": "77450199-1",
       "address": {
           "country": "CL",
           "region": "CL-AN",
           "city": "CL-ANF",
           "address": "Napoleon 3200"
       }
       "tax_information": {
           "activity": "OTRAS ACTIVIDADES DE TECNOLOGIA DE LA INFORMACION Y DE SERVICIOS INFORMATICOS",
           "activity_codes": [
               620200,
               620900,
               702000
           ],
           "resolution_date": "2014-08-22",
           "resolution_number": "80"
       }
   },
   "recipient": {
       "legal_name": "CONSUMIDOR FINAL",
       "document_type": "RUT",
       "document_number": "66666666-6",
       "address": {
           "country": "CL",
           "address": "sin direccion"
       }
   },
   "additional_header_info": {
       "service_indicator": "FS"
   },
   "currency": {
       "code": "CLP",
       "exchange_rate": 1
   },
   "payment_method": {
       "code": "CON",
       "description": "Contado"
   },
   "items": [
       {
           "quantity": 2,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 6,
           "description": "PLAN FULL",
           "taxes": [
               {
                   "type": "CL_GRAV_BAS",
                   "amount": 2,
                   "rate": 19
               }
           ]
       },
       {
           "quantity": 1,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 8,
           "description": "INSTALACION SET BASICO",
           "taxes": [
               {
                   "type": "CL_GRAV_BAS",
                   "amount": 1,
                   "rate": 19
               }
           ]
       }
   ],
   "totals": {
       "sub_total": 17,
       "discount": 0,
       "taxes": [
           {
               "type": "CL_GRAV_BAS",
               "amount": 3,
               "base_amount": 17,
               "rate": 19
           }
       ],
       "total": 20
   }
}

```

</details>

<details>

<summary>Boleta No Afecta o Exenta Electrónica</summary>

```bash
{
   "branch_office": 1,
   "invoice_type": "BOLE",
   "invoice_date": "2025-01-30 16:00:00",
   "payment_due_date": "2025-01-30",
   "external_reference": "1515",
   "issuer": {
       "legal_name": "CONTABILIUM CHILE SPA",
       "document_type": "RUT",
       "document_number": "77450199-1",
       "address": {
           "country": "CL",
           "region": "CL-AN",
           "city": "CL-ANF",
           "address": "Napoleon 3200"
       }
       "tax_information": {
           "activity": "OTRAS ACTIVIDADES DE TECNOLOGIA DE LA INFORMACION Y DE SERVICIOS INFORMATICOS",
           "activity_codes": [
               620200,
               620900,
               702000
           ],
           "resolution_date": "2014-08-22",
           "resolution_number": "80"
       }
   },
   "recipient": {
       "legal_name": "CONSUMIDOR FINAL",
       "document_type": "RUT",
       "document_number": "66666666-6",
       "address": {
           "country": "CL",
           "address": "sin direccion"
       }
   },
   "additional_header_info": {
       "service_indicator": "FS"
   },
   "currency": {
       "code": "CLP",
       "exchange_rate": 1
   },
   "payment_method": {
       "code": "CON",
       "description": "Contado"
   },
   "items": [
       {
           "quantity": 2,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 6,
           "description": "PLAN FULL",
           "taxes": [
               {
                   "type": "CL_EX_IVA",
                   "amount": 0,
                   "rate": 0
               }
           ]
       },
       {
           "quantity": 1,
           "code_unit_of_measure": "u",
           "discount_amount": 0,
           "unit_price": 8,
           "description": "INSTALACION SET BASICO",
           "taxes": [
               {
                   "type": "CL_EX_IVA",
                   "amount": 0,
                   "rate": 0
               }
           ]
       }
   ],
   "totals": {
       "sub_total": 17,
       "discount": 0,
       "taxes": [
           {
               "type": "CL_EX_IVA",
               "amount": 0,
               "base_amount": 17,
               "rate": 0
           }
       ],
       "total": 17
   }
}

```

</details>
