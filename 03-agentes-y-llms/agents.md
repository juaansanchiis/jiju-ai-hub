# Agentes y LLMs

Visión general de frameworks de agentes open-source y cuándo usar cada uno, más librerías ligeras para scripts autónomos en Python.

## Frameworks de agentes open-source

- **LangChain:** Orquestación de LLMs, chains y tools. Útil para prototipos rápidos y pipelines complejos.
- **LangGraph:** Grafos de estado para agentes con control de flujo, ciclos y persistencia. Ideal para agentes con memoria y ramificación.
- **CrewAI:** Equipos de agentes con roles y tareas. Bueno para flujos multi-agente colaborativos.
- **AutoGen:** Conversaciones multi-agente con human-in-the-loop. Fuerte en investigación y experimentación.

### Cuándo usar cada uno

| Framework | Mejor para | Complejidad |
| --- | --- | --- |
| LangChain | Prototipos, chains simples | Baja-Media |
| LangGraph | Agentes con estado y ciclos | Media-Alta |
| CrewAI | Equipos de agentes con roles | Media |
| AutoGen | Investigación multi-agente | Media-Alta |

## Librerías ligeras para scripts autónomos en Python

- **smolagents** (Hugging Face): agentes mínimos con tool calling.
- **pydantic-ai:** Agentes tipados con validación.
- **instructor:** Extracción estructurada con LLMs.
- **litellm:** Abstracción unificada de proveedores (útil para cambiar de modelo sin cambiar código).

## Tabla resumen

| Nombre | Tipo | Enlace | Descripción | Notas |
| --- | --- | --- | --- | --- |
| LangChain | Framework | [langchain.com](https://www.langchain.com/) | Orquestación de LLMs | Prototipos rápidos |
| LangGraph | Framework | [langchain-ai.github.io/langgraph](https://langchain-ai.github.io/langgraph/) | Grafos de estado | Memoria y ciclos |
| CrewAI | Framework | [crewai.com](https://www.crewai.com/) | Equipos de agentes | Multi-agente |
| AutoGen | Framework | [microsoft.github.io/autogen](https://microsoft.github.io/autogen/) | Conversaciones multi-agente | Investigación |
| smolagents | Librería | [huggingface.co/docs/smolagents](https://huggingface.co/docs/smolagents/) | Agentes mínimos | Ligero |
