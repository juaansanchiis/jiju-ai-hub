# LightRAG

Versión súper optimizada y rápida de GraphRAG que puedes correr en local sin gastar una barbaridad de tokens. Mantiene la capacidad de razonamiento sobre grafos pero con mucho menor coste computacional.

- **Tipo:** Framework de RAG con grafos (ligero)
- **Enlace:** [github.com/HKUDS/LightRAG](https://github.com/HKUDS/LightRAG)
- **Licencia:** MIT

## Instalación

```bash
pip install lightrag-hku
```

## Uso básico

```python
from lightrag import LightRAG, QueryParam
from lightrag.llm.openai import gpt_4o_mini_complete, openai_embed

rag = LightRAG(
    working_dir="./lightrag_data",
    llm_model_func=gpt_4o_mini_complete,
    embedding_func=openai_embed,
)
await rag.ainsert("Texto de tus documentos aquí...")

# Consulta local (entidades específicas)
response = await rag.aquery("¿Qué es X?", param=QueryParam(mode="local"))
print(response)

# Consulta global (todo el corpus)
response = await rag.aquery("Resume los temas principales", param=QueryParam(mode="global"))
print(response)
```

## Modos de consulta

| Modo | Descripción |
| --- | --- |
| `local` | Razona sobre entidades específicas y su vecindario |
| `global` | Usa resúmenes de alto nivel del grafo |
| `hybrid` | Combina local + global |
| `naive` | RAG tradicional (solo vectorial) |

## Uso con modelos locales (Ollama)

```python
from lightrag.llm.ollama import ollama_model_complete, ollama_embed

rag = LightRAG(
    working_dir="./lightrag_data",
    llm_model_func=ollama_model_complete,
    embedding_func=ollama_embed,
)
```

## Casos de uso

- RAG con grafos en local sin costes de API.
- Apuntes de carrera con relaciones entre conceptos.
- Documentación técnica con dependencias.
- Prototipado rápido de GraphRAG.

## Ventajas sobre Microsoft GraphRAG

| Aspecto | Microsoft GraphRAG | LightRAG |
| --- | --- | --- |
| Coste de indexación | Alto | Bajo |
| Velocidad | Lenta | Rápida |
| Modelos locales | Limitado | Excelente soporte |
| Comunidad | Microsoft | Académica (HKU) |
| Madurez | Alta | Media |

## Buenas prácticas

1. Usa modelos locales (Ollama) para reducir costes a cero.
2. Empieza con modo `hybrid` para mejor calidad.
3. Ajusta `top_k` para controlar el contexto enviado al LLM.
4. Combina con RAG tradicional (modo `naive`) como fallback.

## Troubleshooting

- **Indexación lenta:** Usa un modelo de embedding más rápido (nomic-embed-text).
- **Respuestas pobres:** Cambia a modo `hybrid` o aumenta `top_k`.
- **Memoria alta:** Reduce el tamaño del corpus o usa chunks más pequeños.
- **Modelo local no responde:** Verifica que Ollama está corriendo y el modelo está descargado.
