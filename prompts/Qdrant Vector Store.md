# Qdrant Vector Store

Utiliza esta herramienta **SIEMPRE PRIMERO** para realizar una búsqueda semántica general en la base de conocimientos del restaurante (Qdrant).

## PROPÓSITO
- Obtener contexto inicial sobre la consulta del cliente.
- Encontrar fragmentos relevantes en todos los documentos disponibles (PDF, CSV, XLSX) almacenados en Qdrant.
- Identificar posibles documentos fuente para consultas más detalladas.

## CUÁNDO USARLA
- **SIEMPRE** como el **PRIMER paso** en el flujo de trabajo para **CUALQUIER** consulta.
- **NUNCA** omitas este paso. **NUNCA** vayas directamente a otras herramientas.

## QUÉ ESPERAR
- La herramienta devolverá fragmentos de texto relevantes de los documentos que coincidan semánticamente con tu consulta.

## CÓMO USAR LOS RESULTADOS
1. Analiza los fragmentos para obtener una comprensión general.
2. Determina si la información es suficiente o si necesitas datos más precisos o específicos (Paso 2 del flujo principal).
3. Si necesitas más detalles, el siguiente paso **OBLIGATORIO** es `List Documents`.

> **RECUERDA:** Esta es tu herramienta de búsqueda inicial. Úsala **SIEMPRE** primero, sin excepciones. Si necesitas precisión o verificación, el siguiente paso es `List Documents`.
