# AnythingLLM

La app definitiva para RAG local. Te permite crear un "Workspace", tirarle todos tus PDFs, conectarlo a tu Ollama local y hacerles preguntas. Todo en local, sin enviar datos a terceros.

- **Tipo:** App de escritorio para RAG local
- **Enlace:** [anythingllm.com](https://anythingllm.com/) / [github.com/Mintplex-Labs/anything-llm](https://github.com/Mintplex-Labs/anything-llm)
- **Licencia:** MIT

## Instalación

1. Descarga desde [anythingllm.com](https://anythingllm.com/download).
2. Instala y abre (compatible con Windows, macOS, Linux).
3. Configura tu proveedor de LLM (Ollama, LM Studio, OpenAI, etc.).

## Cómo funciona

1. Crea un **Workspace** (espacio de trabajo).
2. Sube documentos (PDF, TXT, MD, DOCX, etc.) o conecta fuentes (web, GitHub, etc.).
3. AnythingLLM los procesa, los divide en chunks y los indexa en un vector store.
4. Haz preguntas en el chat; el LLM responde usando el contexto de tus documentos.

## Características principales

- **RAG local:** Todo se procesa en tu máquina (con Ollama/LM Studio).
- **Multi-workspace:** Separa documentos por proyecto/tema.
- **Múltiples LLMs:** OpenAI, Anthropic, Ollama, LM Studio, Azure, etc.
- **Múltiples vector stores:** LanceDB (local), Chroma, Pinecone, Qdrant, etc.
- **Agentes:** Soporte para agentes con tools (búsqueda web, etc.).
- **API REST:** Expone una API para integrar con otros sistemas.
- **Embed widgets:** Incrusta un chatbot en tu web.

## Configuración con Ollama

1. Instala Ollama y descarga un modelo: `ollama pull llama3.1:8b`.
2. En AnythingLLM: Settings → LLM Provider → Ollama.
3. URL: `http://localhost:11434`.
4. Modelo: `llama3.1:8b`.
5. Embedding model: `nomic-embed-text` (o el que prefieras).

## Casos de uso

- Chatbot con tus apuntes de la carrera.
- Asistente de documentación técnica.
- Búsqueda semántica en tus PDFs.
- Base de conocimiento personal.
- RAG para proyectos de código (conecta GitHub).

## Fuentes de datos soportadas

| Fuente | Descripción |
| --- | --- |
| Archivos (PDF, TXT, MD, DOCX) | Subida directa |
| Sitios web | Scraping de URLs |
| GitHub | Repositorios completos |
| YouTube | Transcripciones de vídeos |
| Confluence | Documentación empresarial |
| Obsidian | Notas de Obsidian |

## Buenas prácticas

1. Usa un modelo de embedding dedicado (nomic-embed-text) para mejor calidad.
2. Separa documentos por workspace para mejor precisión.
3. Ajusta el tamaño de chunks según el tipo de documento.
4. Usa modelos potentes (7B+) para respuestas de calidad.
5. Combina con Ollama para privacidad total.

## Troubleshooting

- **Respuestas pobres:** Mejora el modelo de embedding o aumenta chunks.
- **Lentitud:** Usa un modelo más pequeño o reduce el contexto.
- **Documentos no se indexan:** Verifica el formato y tamaño del archivo.
- **Ollama no conecta:** Verifica que Ollama está corriendo en localhost:11434.
- **Memoria alta:** Reduce el número de documentos o usa chunks más pequeños.
