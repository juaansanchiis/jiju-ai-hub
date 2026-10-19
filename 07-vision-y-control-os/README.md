# 👁️ Visión Computacional y Control del Sistema Operativo

Para llevar tus apps de escritorio al siguiente nivel, la IA necesita *ver* la pantalla de tu ordenador y controlarla: detectar botones, iconos y elementos de UI para crear agentes que controlan Windows/Linux/macOS haciendo clics reales sin APIs.

## Tabla de contenidos

- [Microsoft OmniParser](omniparser/README.md)
- [Qwen2.5-VL (Local)](qwen2.5-vl/README.md)

## Herramientas principales

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Microsoft OmniParser | Modelo de visión para UI | [github.com/microsoft/OmniParser](https://github.com/microsoft/OmniParser) | Coge una captura de pantalla, detecta botones/iconos y los convierte en JSON estructurado para agentes de control de SO. |
| Qwen2.5-VL | Modelo multimodal open-source | [github.com/QwenLM/Qwen2.5-VL](https://github.com/QwenLM/Qwen2.5-VL) | El modelo multimodal open-source más potente; analiza vídeos fotograma a fotograma y documentos complejos en local. |

## Otras herramientas relacionadas

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Screenpipe | Grabación de pantalla para IA | [github.com/mediar-ai/screenpipe](https://github.com/mediar-ai/screenpipe) | Graba tu pantalla 24/7 y la indexa para que un LLM la consulte. |
| Open Interpreter | Control del SO por voz/texto | [github.com/OpenInterpreter/open-interpreter](https://github.com/OpenInterpreter/open-interpreter) | Ejecuta código y controla tu ordenador a partir de lenguaje natural. |
| PyAutoGUI | Automatización de GUI | [pyautogui.readthedocs.io](https://pyautogui.readthedocs.io/) | Controla ratón y teclado desde Python; base de agentes de control. |
| UFO (Microsoft) | Agente de escritorio Windows | [github.com/microsoft/UFO](https://github.com/microsoft/UFO) | Agente que controla apps de Windows usando visión + LLM. |
| CogAgent | Modelo de visión para GUI | [github.com/THUDM/CogAgent](https://github.com/THUDM/CogAgent) | Modelo especializado en entender y operar interfaces gráficas. |
| SeeAct | Agente web con visión | [github.com/OSU-NLP-Group/SeeAct](https://github.com/OSU-NLP-Group/SeeAct) | Agente que navega webs usando capturas de pantalla en lugar del DOM. |
| Ferret (Apple) | Modelo de visión referencial | [github.com/apple/ml-ferret](https://github.com/apple/ml-ferret) | Modelo que refiere regiones de imagen con lenguaje natural. |
| LLaVA | Modelo visión-lenguaje | [llava-vl.github.io](https://llava-vl.github.io/) | Modelo open-source de visión-lenguaje, base de muchos agentes visuales. |

## Buenas prácticas

1. Ejecuta los agentes de control de SO en VMs o contenedores para evitar daños.
2. Limita las acciones permitidas (lista blanca de apps/comandos).
3. Registra cada acción con captura de pantalla para auditoría.
4. Usa modelos de visión ligeros (OmniParser) para detección y LLMs grandes solo para razonamiento.
5. Añade confirmación humana para acciones destructivas (borrar, enviar, pagar).
