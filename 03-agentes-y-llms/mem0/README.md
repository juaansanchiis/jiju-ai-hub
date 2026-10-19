# Mem0

Herramienta para darle **memoria a largo plazo** a tus agentes. Para que si usas OpenHands hoy, mañana recuerde cómo te gusta que tabule el código o qué base de datos usaste ayer.

- **Tipo:** Capa de memoria para agentes de IA
- **Enlace:** [github.com/mem0ai/mem0](https://github.com/mem0ai/mem0)
- **Licencia:** Apache 2.0

## Instalación

```bash
pip install mem0ai
```

## Uso básico

```python
from mem0 import Memory

m = Memory()

# Guardar un recuerdo
m.add("El usuario prefiere tabulación de 4 espacios y usa PostgreSQL.", user_id="juan")

# Buscar recuerdos relevantes
results = m.search("¿Cómo le gusta tabular el código al usuario?", user_id="juan")
print(results)
```

## Integración con agentes

```python
from mem0 import Memory
from openai import OpenAI

memory = Memory()
client = OpenAI()

def chat(user_input, user_id):
    # Recuperar contexto relevante
    memories = memory.search(user_input, user_id=user_id)
    context = "\n".join([m["memory"] for m in memories])

    response = client.chat.completions.create(
        model="gpt-4o-mini",
        messages=[
            {"role": "system", "content": f"Contexto del usuario:\n{context}"},
            {"role": "user", "content": user_input},
        ],
    )
    answer = response.choices[0].message.content

    # Guardar la interacción
    memory.add(f"Usuario: {user_input}\nAsistente: {answer}", user_id=user_id)
    return answer
```

## Características clave

- Memoria a largo plazo persistente (vectorial + grafo opcional).
- Búsqueda semántica de recuerdos relevantes.
- Soporte para múltiples usuarios y agentes.
- Integración con LangChain, CrewAI, AutoGen, etc.
- Backend configurable (Qdrant, Chroma, Pinecone, etc.).
- Memoria de grafo (Graph Memory) para relaciones entre entidades.

## Casos de uso

- Agentes que recuerdan preferencias del usuario.
- Asistentes de código que recuerdan estilo y convenciones.
- Chatbots con memoria entre sesiones.
- Agentes de soporte que recuerdan historial de tickets.

## Configuración avanzada

```python
from mem0 import Memory

config = {
    "vector_store": {
        "provider": "qdrant",
        "config": {"host": "localhost", "port": 6333},
    },
    "llm": {
        "provider": "openai",
        "config": {"model": "gpt-4o-mini"},
    },
    "embedder": {
        "provider": "openai",
        "config": {"model": "text-embedding-3-small"},
    },
}
m = Memory.from_config(config)
```

## Buenas prácticas

1. Usa `user_id` para aislar memorias por usuario.
2. Limpia memorias obsoletas periódicamente.
3. Combina con RAG para documentos + memoria de conversación.
4. Usa Graph Memory para relaciones complejas.
5. Monitoriza el tamaño de la base de vectores.

## Troubleshooting

- **Memorias irrelevantes:** Mejora los prompts de extracción.
- **Búsqueda lenta:** Usa un vector store optimizado (Qdrant).
- **Duplicados:** Activa deduplicación en la configuración.
- **Coste alto:** Usa modelos baratos para extracción de memorias.
- **Memoria no persiste:** Verifica la configuración del vector store.
