# Rate limit y paginado

### 📌 **Rate Limit**

Nuestra API implementa límites de tasa (_Rate Limiting_) para garantizar un uso equitativo y mantener la estabilidad del servicio.

#### 🔹 **Límites de solicitudes**

Los valores actuales son:

* **Límite por segundo:** 50 solicitudes
* **Límite por minuto:** 3000 solicitudes

⚠️ Si se exceden estos límites, la API devolverá un código de estado **`429 Too Many Requests`**, junto con un encabezado `Retry-After` indicando el tiempo en segundos que se debe esperar antes de realizar nuevas solicitudes.

***

### 📌 **Paginado**

Para mejorar la eficiencia en la recuperación de datos, nuestra API utiliza un mecanismo de paginación basado en 100 resultados como máximo por página y el parámetro page para indicar el número de página.

#### 🔹 **Parámetros de paginación**

Al realizar una solicitud a los endpoints que soportan paginado, puedes utilizar los siguientes parámetros:

* **`{parametro_offset}`** → Especifica el índice desde el cual empezar la consulta.

Ejemplo de solicitud paginada:

```http
GET /invoice/list?{parametro_offset}=XX&{parametro_limit}=XX
```

#### 🔹 **Respuesta paginada**

Cada respuesta incluirá información sobre la paginación en el cuerpo de la respuesta o en los encabezados:

```json
{ ...,
  "total": {total_elementos},
  "limit": 100,
  "offset": {valor_offset},
  "data": [
    {...}, {...}
  ],
  "next": "{url_siguiente_pagina}",
  "previous": "{url_pagina_anterior}"
}
```

Donde:

* **`total`** → Cantidad total de registros disponibles.
* **`limit`** → Número de registros devueltos en esta página. Valor fijo de 100 resultados máximos.¿.
* **`offset`** → Índice del primer elemento en la página actual.
* **`data`** → Conjunto de registros devueltos.
* **`next`** → URL de la siguiente página (si existe).
* **`previous`** → URL de la página anterior (si existe).
