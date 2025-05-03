# Get File Contents

Realiza una consulta HTTP a la API de Qdrant para recuperar fragmentos de texto más específicos y relevantes de un documento, usando su ID y filtros adicionales. **Usar SOLO DESPUÉS de `List Documents`.**

## FLUJO DE TRABAJO OBLIGATORIO:

1. NUNCA usar directamente o después de RAG.  
2. USAR OBLIGATORIAMENTE como Paso 4 del flujo principal si se necesita recuperar fragmentos precisos de documentos no tabulares (ej. PDFs) y RAG inicial fue insuficiente.  
3. **REQUISITO INDISPENSABLE:** Debes haber obtenido el `id` del documento mediante `List Documents` en el Paso 3 inmediatamente anterior.  
4. NUNCA omitir el paso de `List Documents`, incluso si RAG proporcionó metadatos como ID.

## CUÁNDO USARLA:

* Necesitas información más específica de documentos de texto (PDFs como Políticas, FAQs, Servicios Especiales) que los fragmentos generales de RAG.  
* Quieres filtrar fragmentos dentro de un documento específico (`id`) basándote en palabras clave, contexto o criterios adicionales que la API de Qdrant permita.  
* `Query Document Rows` no aplica (no es un archivo tabular).

## PARÁMETROS PROBABLES (Basado en el nodo HTTP y API Qdrant):

- `file_id` o similar: ID del documento (OBLIGATORIO, obtenido de `List Documents`) para filtrar la búsqueda en Qdrant.  
- `query` o `keywords`: Términos de búsqueda para encontrar fragmentos relevantes dentro de ese documento.  
- Otros filtros posibles: Parámetros adicionales que la API de Qdrant acepte para refinar la búsqueda de puntos/vectores.

## QUÉ ESPERAR:

- Una lista de fragmentos de texto (chunks) más específicos y relevantes del documento solicitado, recuperados directamente de Qdrant.

## CÓMO USAR LOS RESULTADOS:

1. Analiza los fragmentos específicos devueltos.  
2. Verifica si contienen la información precisa que buscabas.  
3. Sintetiza la respuesta final basada en estos fragmentos más precisos.

## MEJORES PRÁCTICAS:

- Úsala como un paso de refinamiento cuando RAG fue demasiado general pero necesitas información de un documento específico no tabular.  
- Formula filtros o palabras clave precisas para obtener los mejores fragmentos.

**RECUERDA:** Esta herramienta consulta Qdrant vía HTTP para obtener fragmentos precisos de un documento específico. Úsala SOLO después de `List Documents` cuando necesites refinar la búsqueda en documentos no tabulares.
