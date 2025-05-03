# Agentic RAG en n8n explicado a fondo

**Repositorio oficial del proyecto mostrado en la serie de videos _"Agentic RAG en n8n"_ publicada en YouTube.** Aquí encontrarás los archivos `.md` explicativos, flujos en formato JSON, configuraciones de Docker, y más recursos técnicos para implementar una arquitectura Agentic RAG completamente funcional utilizando [n8n](https://n8n.io/), [Qdrant](https://qdrant.tech/) y PostgreSQL.

---

## 🎥 Serie completa en YouTube

> Esta serie explora cómo construir un agente inteligente que utiliza recuperación aumentada por generación (RAG) con razonamiento paso a paso, ejecutando flujos complejos en un entorno **100% no-code**.

### ▸ [Parte 1 – Fundamentos teóricos de Agentic RAG](https://youtu.be/LJpLK6zAr7w)
Fundamentos conceptuales del enfoque Agentic RAG, estructura general y decisiones clave del diseño.

### ▸ [Parte 2 – Preparación del entorno y credenciales](https://youtu.be/3VI3Puc3Iqs)
Configuración del entorno local usando Docker Compose: n8n, PostgreSQL, Redis, Qdrant y herramientas de monitoreo.

### ▸ [Parte 3 – Vectorización y estructura de datos](https://youtu.be/OS8OTLGJfyg)
Proceso de vectorización de documentos, ingreso en Qdrant y estructuración de datos tabulares en PostgreSQL.

### ✅ [Parte 4 – Agentic RAG en acción](https://youtu.be/U1M2rxpwOyI)
El agente toma decisiones en tiempo real: cuándo usar Qdrant, cuándo consultar PostgreSQL, cómo manejar preguntas ambiguas, y más.


## 🚀 ¿Cómo utilizar los archivos?

1. **Lee los archivos `.md`** para comprender cada paso de la implementación.
2. **Configura tu entorno** siguiendo las instrucciones de `02_entorno_local.md`.
3. **Crea los flujos en n8n** basados en los ejemplos de cada archivo.
4. **Prueba el sistema** y ajusta la lógica según sea necesario.

---

## ⚙️ Tecnologías y Herramientas

- **n8n**: Herramienta de automatización no-code.
- **PostgreSQL**: Base de datos estructurada para datos tabulares.
- **Qdrant**: Base de datos vectorial para búsquedas semánticas.
- **Redis**: Manejo de cola de ejecución de workers en n8n.

---

## 💬 Contacto Técnico

Si tienes preguntas técnicas o deseas colaborar, no dudes en ponerte en contacto con el equipo a través de:

**Email:** [devcloudplanet@gmail.com](mailto:devcloudplanet@gmail.com)

---
