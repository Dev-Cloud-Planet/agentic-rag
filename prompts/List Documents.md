# List Documents

Utilice esta herramienta para obtener los metadatos de TODOS los documentos disponibles desde Postgres. **Paso OBLIGATORIO y ÚNICO después de determinar que RAG inicial fue insuficiente y ANTES de usar `Query Document Rows` o `Get File Contents`.**

## FLUJO DE TRABAJO OBLIGATORIO:

1. NUNCA usar como primera acción (RAG es siempre primero).  
2. USAR OBLIGATORIAMENTE si el Paso 2 del flujo principal determinó la necesidad de precisión.  
3. USAR INMEDIATAMENTE ANTES de decidir entre `Query Document Rows` o `Get File Contents`.  
4. NUNCA omitir este paso, incluso si RAG proporcionó metadatos como ID.

## PROPÓSITO CRÍTICO:

1. **Identificar Documentos**: Encuentra el/los documento(s) relevante(s) por `title`.  
2. **Obtener ID**: Recupera el `id` exacto del/los documento(s). Este ID es OBLIGATORIO para el *siguiente* paso (`Query Document Rows` o `Get File Contents`).  
3. **OBTENER SCHEMA (¡FUNDAMENTAL!)**: Para archivos tabulares (CSV, XLSX), devuelve el `schema` (lista exacta de nombres de columnas, ej: "Categoria, Nombre, Descripcion, Precio"). Esta información es ESENCIAL y DEBE ser usada para construir la consulta SQL en el *siguiente* paso si se elige `Query Document Rows`.

La herramienta devolverá una lista de documentos con `id`, `title`, `url`, `created_at`, `schema`.

**ACCIÓN INMEDIATA POSTERIOR:** Una vez obtenidos el `id` (y `schema` si aplica), procede INMEDIATAMENTE al Paso 4 del flujo principal para usar `Query Document Rows` o `Get File Contents`.

**RECUERDA:** Esta herramienta es el PUENTE INDISPENSABLE hacia los datos precisos. NUNCA la omitas. NUNCA vayas directamente de RAG a `Query Document Rows` o `Get File Contents`.
