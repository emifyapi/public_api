# Rate limit y paginado

### 📌 **Rate Limit**

Nuestra API implementa límites de tasa (_Rate Limiting_) para garantizar un uso equitativo y mantener la estabilidad del servicio.

#### 🔹 **Límites de solicitudes**

Los valores actuales son:

* **Límite por segundo:** `XX` solicitudes
* **Límite por minuto:** `XX` solicitudes
* **Límite por hora:** `XX` solicitudes
* **Límite por día:** `XX` solicitudes

⚠️ Si se exceden estos límites, la API devolverá un código de estado **`429 Too Many Requests`**, junto con un encabezado `Retry-After` indicando el tiempo en segundos que se debe esperar antes de realizar nuevas solicitudes.

#### 🔹 **Encabezados de Rate Limit**

En cada respuesta de la API, incluimos encabezados para informar el estado del uso de la cuota:

```http
httpCopiarEditarX-Rate-Limit-Limit: {valor_máximo_permitido}
X-Rate-Limit-Remaining: {solicitudes_restantes}
X-Rate-Limit-Reset: {timestamp_reset}
```

Donde:

* **`X-Rate-Limit-Limit`** → Indica el número total de solicitudes permitidas en el período de tiempo.
* **`X-Rate-Limit-Remaining`** → Muestra cuántas solicitudes quedan antes de alcanzar el límite.
* **`X-Rate-Limit-Reset`** → Tiempo UNIX en que se restablece el límite.

***

### 📌 **Paginado**

Para mejorar la eficiencia en la recuperación de datos, nuestra API utiliza un mecanismo de paginación basado en **{método de paginado, ej. "offset-limit", "cursor-based", etc.}**.

#### 🔹 **Parámetros de paginación**

Al realizar una solicitud a los endpoints que soportan paginado, puedes utilizar los siguientes parámetros:

* **`{parametro_offset}`** → Especifica el índice desde el cual empezar la consulta.
* **`{parametro_limit}`** → Define el número de registros devueltos por página (máximo: `{valor_máximo}`).
* _(Opcional: agregar otros parámetros si aplica, como ordenamiento o filtrado)_

Ejemplo de solicitud paginada:

```http
GET /invoice/list?{parametro_offset}=XX&{parametro_limit}=XX
```

#### 🔹 **Respuesta paginada**

Cada respuesta incluirá información sobre la paginación en el cuerpo de la respuesta o en los encabezados:

```json
{ ...,
  "total": {total_elementos},
  "limit": {valor_limit},
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
* **`limit`** → Número de registros devueltos en esta página.
* **`offset`** → Índice del primer elemento en la página actual.
* **`data`** → Conjunto de registros devueltos.
* **`next`** → URL de la siguiente página (si existe).
* **`previous`** → URL de la página anterior (si existe).
