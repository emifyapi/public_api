# Rate limit y paginado

### 📌 **Rate Limit**

Nuestra API implementa límites de tasa (_Rate Limit_) para garantizar un uso equitativo y mantener la estabilidad del servicio.

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

* **`{page}`** → Especifica el índice desde el cual empezar la consulta.

Ejemplo de solicitud paginada:

```http
GET /invoice/list?{page}
```

#### 🔹 **Respuesta paginada**

Cada respuesta incluirá información sobre la paginación en el cuerpo de la respuesta o en los encabezados:

```json
{   "page": 1,
    "total_pages": 2,
    "total_results": 85,
    "data": [
    {...}, {...}
  ]
}
```

Donde:

* **`total_pages`** → Cantidad total de páginas disponibles.
* **`total_results`** → Número de registros devueltos en esta página. Valor máximo fijo de 100 resultados por página.
* **`page`**→ número de página actual.
* **`data`** → Conjunto de registros devueltos.

