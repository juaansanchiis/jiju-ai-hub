# Microsoft GraphRAG

Framework de RAG con grafos de conocimiento de Microsoft. Extrae entidades de tus documentos y crea un mapa mental gigante (un grafo). En lugar de buscar "palabras similares", el LLM razona sobre las conexiones. Ideal si le metes apuntes enteros de la carrera y le pides que relacione conceptos.

- **Tipo:** Framework de RAG con grafos
- **Enlace:** [github.com/microsoft/graphrag](https://github.com/microsoft/graphrag)
- **Licencia:** MIT

## Instalación

```bash
pip install graphrag
```

## Flujo de trabajo

1. **Indexación:** Procesa tus documentos, extrae entidades y relaciones, construye el grafo.
2. **Query (Global):** Responde preguntas sobre todo el corpus usando resúmenes de comunidades del grafo.
3. **Query (Local):** Responde preguntas sobre entidades específicas usando su vecindario en el grafo.

## Configuración inicial

```bash
mkdir -p ./ragtest/input
# Copia tus documentos (.txt, .md) a ./ragtest/input
graphrag init --root ./ragtest
```

## Indexación

```bash
graphrag index --root ./ragtest
```

## Consulta global

```bash
graphrag query --root ./ragtest --method global "¿Cuáles son los temas principales del corpus?"
```

## Consulta local

```bash
graphrag query --root ./ragtest --method local "Explica la relación entre X e Y"
```

## Configuración (settings.yaml)

```yaml
llm:
  api_key: ${GRAPHRAG_API_KEY}
  type: openai_chat
  model: gpt-4o-mini
  model_supports_json: true
  max_tokens: 4000

embeddings:
  async_mode: threaded
  llm:
    api_key: ${GRAPHRAG_API_KEY}
    type: openai_embedding
    model: text-embedding-3-small

chunks:
  size: 1200
  overlap: 100
```

## Casos de uso

- Apuntes de carrera (relacionar conceptos de distintas asignaturas).
- Papers científicos (encontrar conexiones entre investigaciones).
- Código (entender dependencias y arquitectura).
- Documentación técnica extensa.

## Costes y limitaciones

- La indexación consume muchos tokens (LLM para extracción de entidades).
- Usa modelos baratos (gpt-4o-mini) para indexación y modelos potentes para query.
- El grafo puede crecer mucho; limita el tamaño del corpus.

## Buenas prácticas

1. Usa modelos baratos para indexación y potentes para consultas.
2. Empieza con un corpus pequeño para calibrar costes.
3. Revisa el grafo generado (GraphML) para validar la extracción.
4. Combina con RAG tradicional para preguntas factuales simples.

## Troubleshooting

- **Indexación falla:** Verifica la API key y el formato de los documentos.
- **Respuestas vagas:** Aumenta el número de comunidades en la query global.
- **Coste alto:** Reduce el tamaño de chunks o usa modelos más baratos.
- **Grafo vacío:** Asegúrate de que los documentos tienen entidades claras.
