# Zep (Graphiti)

Herramienta para darle **memoria a largo plazo** a tus agentes con grafos de conocimiento temporales. Para que si usas OpenHands hoy, mañana recuerde cómo te gusta que tabule el código o qué base de datos usaste ayer.

- **Tipo:** Memoria a largo plazo con grafos temporales
- **Enlace:** [github.com/getzep/zep](https://github.com/getzep/zep) / [github.com/getzep/graphiti](https://github.com/getzep/graphiti)
- **Licencia:** Apache 2.0

## Conceptos clave

- **Memory:** Almacena mensajes de conversación y los extrae en un grafo de conocimiento.
- **Graphiti:** Motor de grafos temporales que rastrea cómo cambian las relaciones a lo largo del tiempo.
- **Session:** Una conversación con un usuario; Zep extrae entidades y relaciones automáticamente.
- **Fact:** Un hecho extraído del grafo (ej. "El usuario usa PostgreSQL").

## Instalación (Zep Cloud / Self-hosted)

```bash
# Self-hosted con Docker
docker compose up -d
# O usa Zep Cloud: https://www.getzep.com/
```

```bash
pip install zep-python
```

## Uso básico (Python SDK)

```python
from zep_python import ZepClient

client = ZepClient(api_key="tu_api_key")

# Crear una sesión
session = client.memory.add_session(
    session_id="session_1",
    user_id="juan",
)

# Añadir mensajes
client.memory.add(
    session_id="session_1",
    messages=[
        {"role": "user", "content": "Prefiero tabulación de 4 espacios y uso PostgreSQL."},
        {"role": "assistant", "content": "Entendido, usaré 4 espacios y PostgreSQL."},
    ],
)

# Buscar memoria relevante
results = client.memory.search(
    session_id="session_1",
    text="¿Cómo le gusta tabular el código?",
    limit=5,
)
for r in results:
    print(r.message.content)
```

## Graphiti (motor de grafos)

```python
from graphiti_core import Graphiti

graphiti = Graphiti("bolt://localhost:7687", "neo4j", "password")

# Añadir un episodio (conversación)
await graphiti.add_episode(
    name="conversacion_1",
    episode_body="El usuario prefiere 4 espacios y usa PostgreSQL.",
    source_description="chat",
)

# Buscar hechos relevantes
results = await graphiti.search("preferencias de código del usuario")
for r in results:
    print(r.fact)
```

## Características clave

- Grafos de conocimiento temporales (rastrea cambios a lo largo del tiempo).
- Extracción automática de entidades y relaciones.
- Búsqueda semántica + por grafo.
- Integración con LangChain, LlamaIndex, etc.
- Self-hosted (Docker) o cloud.
- Soporte para múltiples usuarios y sesiones.

## Casos de uso

- Agentes que recuerdan preferencias y contexto a largo plazo.
- Asistentes que rastrean cómo cambian las preferencias del usuario.
- Sistemas de soporte con memoria de tickets anteriores.
- Agentes de código que recuerdan convenciones del proyecto.

## Comparación Mem0 vs Zep

| Aspecto | Mem0 | Zep (Graphiti) |
| --- | --- | --- |
| Tipo de memoria | Vectorial + grafo opcional | Grafo temporal nativo |
| Complejidad | Baja | Media-Alta |
| Self-hosted | Sí (vector store) | Sí (Neo4j + Docker) |
| Cloud | Sí (Mem0 Cloud) | Sí (Zep Cloud) |
| Temporalidad | No nativa | Sí (rastrea cambios) |
| Integraciones | LangChain, CrewAI, etc. | LangChain, LlamaIndex |
| Mejor para | Memoria simple y rápida | Memoria compleja con relaciones |

## Buenas prácticas

1. Usa sesiones separadas por usuario para aislar memorias.
2. Limpia sesiones antiguas para controlar el tamaño del grafo.
3. Combina con RAG para documentos + memoria de conversación.
4. Usa Graphiti para relaciones complejas entre entidades.
5. Monitoriza el uso de Neo4j (memoria y CPU).

## Troubleshooting

- **Grafo vacío:** Verifica que los mensajes se están añadiendo correctamente.
- **Búsqueda lenta:** Optimiza los índices de Neo4j.
- **Memoria no persiste:** Verifica la conexión a la base de datos.
- **Coste alto:** Usa modelos baratos para extracción de entidades.
- **Duplicados:** Activa deduplicación en Graphiti.
