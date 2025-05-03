# Query Document Rows

Ejecutar una consulta SQL **sintácticamente PERFECTA** para extraer datos específicos y estructurados de archivos tabulares (CSV, XLSX) almacenados en Postgres. **Usar SOLO DESPUÉS de `List Documents`.**

## FLUJO DE TRABAJO OBLIGATORIO:

1. NUNCA usar directamente o después de RAG.  
2. USAR OBLIGATORIAMENTE como Paso 4 del flujo principal si se necesita consultar datos tabulares.  
3. **REQUISITO INDISPENSABLE:** Debes haber obtenido el `id` y el `schema` del documento tabular mediante `List Documents` en el Paso 3 inmediatamente anterior.  
4. NUNCA omitir el paso de `List Documents`, incluso si RAG proporcionó metadatos como ID.

## CRITICAL SQL SYNTAX RULE 1: QUOTES

* **ALWAYS use SINGLE QUOTES (`'`) for string literals.**  
* **NEVER use DOUBLE QUOTES (`"`) for string literals.**  
* **Correct Example:** `WHERE dataset_id = 'abc-123' AND row_data->>'Categoria' = 'Postres'`

## CRITICAL SQL SYNTAX RULE 2: ALIASES (MUST USE!)

* **You MUST use an explicit alias (e.g., `AS alias_name`) for EVERY column you select using `row_data->>'ColumnName'`.**  
* **Correct Example:** `SELECT row_data->>'Nombre' AS nombre_plato, row_data->>'Precio' AS precio_plato ...`

## CRITICAL SQL SYNTAX RULE 3: NUMERIC CASTING (PARENTHESES REQUIRED!)

* **When comparing or ordering by a numeric value stored as text (e.g., 'Precio'), you MUST enclose the field extraction in parentheses `()` BEFORE casting to `::numeric` or `::float`.**  
* **Correct Example (Filtering):** `... WHERE (row_data->>'Precio')::numeric < 10`  
* **Correct Example (Ordering):** `... ORDER BY (row_data->>'Precio')::numeric ASC`  
* **Incorrect Example (WILL FAIL):** `... WHERE row_data->>'Precio'::numeric < 10`  
* **Incorrect Example (WILL FAIL):** `... ORDER BY row_data->>'Precio'::numeric ASC`

## CÓMO CONSTRUIR LA CONSULTA SQL (Inteligencia de Schema + Sintaxis Correcta):

1. Usa el `id` obtenido en la cláusula `WHERE dataset_id = '[ID_OBTENIDO_CON_COMILLAS_SIMPLES]'`.  
2. Examina el `schema` obtenido de `List Documents` (ej: `"Categoria, Nombre, Descripcion, Precio"`).  
3. **Identifica inteligentemente** qué nombres de columna del `schema` son necesarios.  
4. **CRUCIAL: Usa los nombres de columna EXACTOS del `schema` obtenido de `List Documents`** para acceder a `row_data` (ej: `row_data->>'Nombre'`, `row_data->>'Precio'`). **NO inventes nombres de columna.**  
5. **APLICA LA REGLA CRÍTICA DE ALIAS:** Añade `AS alias_descriptivo` a **CADA** columna seleccionada.  
6. **APLICA LA REGLA CRÍTICA DE COMILLAS:** Usa **comillas simples (`'`)** para todos los valores de texto en `WHERE` o `ILIKE`.  
7. **APLICA LA REGLA CRÍTICA DE CASTING NUMÉRICO:** Usa **paréntesis `()`** antes de `::numeric` o `::float` si comparas u ordenas por un número almacenado como texto.

## ESTRUCTURA DE LA TABLA `document_rows`:

- `dataset_id`: ID del archivo (obtenido de `List Documents`).  
- `row_data`: JSONB que contiene los datos de la fila, con claves que coinciden EXACTAMENTE con los nombres de columna del `schema`.

## RECUERDA:

1. El `id` y el `schema` de `List Documents` (paso anterior) son OBLIGATORIOS.  
2. El agente DEBE usar inteligentemente el `schema` para elegir y escribir los nombres de columna correctos (`row_data->>'NombreColumnaDelSchema'`).  
3. **LA SINTAXIS SQL DEBE SER PERFECTA: COMILLAS SIMPLES (`'`) PARA STRINGS, ALIAS (`AS ...`) PARA CADA COLUMNA SELECCIONADA, Y PARÉNTESIS `()` ANTES DE CASTING NUMÉRICO (`::numeric`).**  
4. **NUNCA OMITAS EL PASO DE `List Documents`.**
