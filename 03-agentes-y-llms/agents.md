# 🤖 AI Agents & LLMs Hub

Recopilación de frameworks, arquitecturas de razonamiento autónomo, patrones de diseño multi-agente y metodologías para desplegar agentes de software inteligentes capaces de interactuar con terminales, repositorios de código y APIs.

---

## 1. Arquitecturas de Agentes Autónomos

Principales patrones de diseño utilizados para estructurar el comportamiento de un LLM cuando se le otorga autonomía operativa:

- **ReAct (Reason + Act):** El agente alterna iterativamente entre razonar sobre el estado actual (`Thought`), decidir una acción (`Action`) y observar el resultado (`Observation`) antes de dar la respuesta final.
- **Plan-and-Execute (Planificar y Ejecutar):** El agente descompone una tarea compleja en un grafo de subtareas secuenciales o paralelas antes de empezar a escribir código o ejecutar comandos.
- **Reflection / Self-Correction:** El agente evalúa su propio código o salidas (mediante tests unitarios, análisis estático o un modelo crítico secundario) y corrige los errores de forma iterativa antes de reportar el resultado.
- **Tool Use / Function Calling:** El LLM decide qué herramientas invocar (terminal, filesystem, APIs) y con qué parámetros, recibiendo los resultados para continuar.
- **Multi-Agent (Crew/Debate):** Varios agentes con roles especializados colaboran o debaten para resolver una tarea.

---

## 2. Frameworks de Orquestación Principales

- **Aider (`aider/`):** El estándar de la industria para desarrollo asistido por IA directamente desde la línea de comandos conectada a Git.
- **Cline / ex-Claude Dev (`cline/`):** Asistente autónomo dentro de VS Code con permisos avanzados para modificar archivos, ejecutar terminal y manejar herramientas de workspace.
- **OpenHands / ex-OpenDevin (`openhands/`):** Ingeniero de software de código abierto autónomo desplegable en Docker con capacidades completas de navegación web y terminal.
- **Hermes Agent (`hermes-agent/`):** Agente optimizado para ejecución profunda de tareas de sistema y automatización avanzada.

### Otros frameworks de orquestación

- **LangChain:** Orquestación de LLMs, chains y tools. Útil para prototipos rápidos y pipelines complejos.
- **LangGraph:** Grafos de estado para agentes con control de flujo, ciclos y persistencia. Ideal para agentes con memoria y ramificación.
- **CrewAI:** Equipos de agentes con roles y tareas. Bueno para flujos multi-agente colaborativos.
- **AutoGen:** Conversaciones multi-agente con human-in-the-loop. Fuerte en investigación y experimentación.
- **SWE-agent:** Agente especializado en resolver issues de GitHub de forma autónoma.
- **Devin (Cognition):** Agente de software comercial con capacidades end-to-end (de pago).

### Cuándo usar cada uno

| Framework | Mejor para | Complejidad |
| --- | --- | --- |
| Aider | Desarrollo en terminal con Git | Baja |
| Cline | Desarrollo en VS Code | Baja-Media |
| OpenHands | Ingeniería end-to-end en Docker | Media |
| Hermes Agent | Automatización profunda de sistema | Media |
| LangChain | Prototipos, chains simples | Baja-Media |
| LangGraph | Agentes con estado y ciclos | Media-Alta |
| CrewAI | Equipos de agentes con roles | Media |
| AutoGen | Investigación multi-agente | Media-Alta |
| SWE-agent | Resolver issues de GitHub | Media |

---

## 3. Librerías ligeras para scripts autónomos en Python

- **smolagents** (Hugging Face): agentes mínimos con tool calling.
- **pydantic-ai:** Agentes tipados con validación.
- **instructor:** Extracción estructurada con LLMs.
- **litellm:** Abstracción unificada de proveedores (útil para cambiar de modelo sin cambiar código).
- **openai / anthropic SDKs:** Clientes oficiales para tool calling.

---

## 4. Patrones y Consejos para Desarrollar con Agentes

1. **Sandboxing (Aislamiento):** Ejecuta siempre a los agentes de código dentro de contenedores Docker o entornos virtuales aislados para evitar daños accidentales en el sistema operativo host.
2. **Límites de Iteración (Max Steps):** Configura siempre un tope estricto de iteraciones por tarea para evitar bucles infinitos donde el agente intente corregir un error de sintaxis una y otra vez quemando tokens.
3. **Uso de Modelos Especializados:** Utiliza modelos con capacidades superiores de razonamiento y seguimiento de instrucciones para la toma de decisiones del agente (como modelos de la familia Qwen Coder o variantes avanzadas), y modelos más económicos o locales para subtareas repetitivas.
4. **Human-in-the-loop:** Mantén aprobación humana para acciones destructivas (borrado, push, deploy).
5. **Observabilidad:** Registra thoughts, actions y observations para depurar y auditar.
6. **Tests como oráculo:** Usa tests unitarios como señal de éxito para que el agente se auto-corrija.

---

## Tabla resumen

| Nombre | Tipo | Enlace | Descripción | Notas |
| --- | --- | --- | --- | --- |
| Aider | Agente CLI | [aider.chat](https://aider.chat/) | Desarrollo asistido en terminal | Conectado a Git |
| Cline | Extensión VS Code | [github.com/cline/cline](https://github.com/cline/cline) | Agente autónomo en IDE | Permisos avanzados |
| OpenHands | Framework | [github.com/All-Hands-AI/OpenHands](https://github.com/All-Hands-AI/OpenHands) | Ingeniero de software autónomo | Docker |
| Hermes Agent | Agente | — | Automatización profunda | Terminal/sistema |
| LangChain | Framework | [langchain.com](https://www.langchain.com/) | Orquestación de LLMs | Prototipos |
| LangGraph | Framework | [langchain-ai.github.io/langgraph](https://langchain-ai.github.io/langgraph/) | Grafos de estado | Memoria y ciclos |
| CrewAI | Framework | [crewai.com](https://www.crewai.com/) | Equipos de agentes | Multi-agente |
| AutoGen | Framework | [microsoft.github.io/autogen](https://microsoft.github.io/autogen/) | Conversaciones multi-agente | Investigación |
| SWE-agent | Agente | [github.com/princeton-nlp/SWE-agent](https://github.com/princeton-nlp/SWE-agent) | Resolver issues de GitHub | Autónomo |
| smolagents | Librería | [huggingface.co/docs/smolagents](https://huggingface.co/docs/smolagents/) | Agentes mínimos | Ligero |
