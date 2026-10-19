# Swarm (OpenAI)

Framework experimental de OpenAI. Súper ligero y fácil para crear sistemas multi-agente en Python. Básicamente creas un agente "Recepcionista" que, dependiendo de lo que le pidas, le pasa la conversación y el contexto a un agente "Programador" o a un "Buscador web".

- **Tipo:** Framework multi-agente (experimental)
- **Enlace:** [github.com/openai/swarm](https://github.com/openai/swarm)
- **Licencia:** MIT

## Instalación

```bash
pip install git+https://github.com/openai/swarm.git
```

## Conceptos clave

- **Agent:** Un agente con instrucciones, funciones (tools) y un modelo.
- **Handoff:** Un agente puede transferir la conversación a otro agente.
- **Function:** Herramientas que el agente puede invocar.
- **Context:** Variables compartidas entre agentes.

## Ejemplo básico

```python
from swarm import Swarm, Agent

client = Swarm()

def transfer_to_programmer():
    return programmer_agent

def transfer_to_researcher():
    return researcher_agent

receptionist = Agent(
    name="Recepcionista",
    instructions="Eres un recepcionista. Si el usuario pregunta sobre código, transfiere al programador. Si pregunta sobre información, transfiere al investigador.",
    functions=[transfer_to_programmer, transfer_to_researcher],
)

programmer = Agent(
    name="Programador",
    instructions="Eres un programador experto. Ayuda con código y desarrollo.",
)

researcher = Agent(
    name="Investigador",
    instructions="Eres un investigador. Busca información y responde preguntas factuales.",
)

response = client.run(
    agent=receptionist,
    messages=[{"role": "user", "content": "¿Cómo hago un bucle en Python?"}],
)
print(response.messages[-1]["content"])
```

## Casos de uso

- Sistemas de atención al cliente con escalado a especialistas.
- Pipelines de desarrollo (planificador → programador → revisor).
- Asistentes con múltiples dominios de conocimiento.
- Prototipado rápido de sistemas multi-agente.

## Ventajas

- Extremadamente simple (pocas líneas de código).
- Handoffs nativos entre agentes.
- Compatible con cualquier modelo de OpenAI.
- Sin dependencias pesadas.

## Limitaciones

- Experimental (no recomendado para producción).
- Sin persistencia de estado entre sesiones.
- Sin memoria a largo plazo integrada.
- Solo soporta modelos de OpenAI (o compatibles).

## Buenas prácticas

1. Mantén las instrucciones de cada agente claras y específicas.
2. Usa handoffs para delegar, no para encadenar lógica compleja.
3. Combina con Mem0/Zep para añadir memoria a largo plazo.
4. Usa funciones (tools) para acciones concretas (APIs, filesystem).
5. Prueba con modelos baratos (gpt-4o-mini) antes de usar gpt-4o.

## Troubleshooting

- **Handoff no funciona:** Verifica que la función devuelve el agente correcto.
- **Contexto perdido:** Swarm no persiste estado; usa variables externas.
- **Modelo no soportado:** Usa modelos de OpenAI o compatibles (Azure, OpenRouter).
- **Respuestas inconsistentes:** Mejora las instrucciones del agente recepcionista.
