# 🎬 AI Video, Multimedia & Generation Hub

Recopilación definitiva de herramientas gratuitas, plataformas web cloud, alternativas locales (Self-Hosted), plugins de automatización por código y conectores multimedia para IA.

---

## 1. Plataformas Web Cloud (Estilo Pavo AI y Freemium Potentes)

Herramientas web con modelos propios o sistemas generativos que ofrecen cuotas gratuitas generosas para vídeo e imagen.

- **Pavo AI (`app.pavo-ai.work`):** Plataforma todo en uno basada en modelos propios (como Agnes) excelente para generación de texto a vídeo, clips cortos, modelado de escenas dinámicas e imágenes con muy pocas restricciones iniciales.
- **Kling AI:** Potente generación de vídeo cinemático con créditos diarios gratuitos. Destaca en físicas de movimiento de cámara y realismo de personajes.
- **Luma Dream Machine:** Generación de vídeo text-to-video e image-to-video con pruebas gratuitas mediante login con cuenta de Google.
- **RunwayML (Gen-3 Alpha):** El estándar de la industria; ofrece créditos de prueba gratuitos ideales para clips cortos de alta fidelidad.
- **PixVerse / Hailuo AI (Minimax):** Alternativas con excelente fluidez de movimiento y opciones gratuitas muy amplias desde web.

---

## 2. Generación de Imágenes Gratis (Webs & APIs)

- **Civitai:** La mayor comunidad de modelos open-source (Stable Diffusion, FLUX). Permite generar imágenes directamente en la nube de forma gratuita con una gran variedad de modelos base y LoRAs.
- **Hugging Face Spaces:** Aloja infinidad de spaces públicos gratuitos para probar modelos punteros como *FLUX.1 [schnell]* o *SD3* sin GPU propia.
- **Tensor.Art:** Plataforma web con cuota diaria gratuita para ejecutar modelos de difusión avanzados y entrenar LoRAs propios en la nube.
- **Leonardo.ai:** Ofrece un reseteo diario de 150 créditos gratuitos, perfecto para producción rápida de conceptos, texturas e imágenes optimizadas.

---

## 3. Ejecución Local (Self-Hosted & Open Source)

Herramientas para correr modelos multimedia de forma local en tu propia GPU (ideal para tarjetas Nvidia con buena VRAM).

- **ComfyUI:** El estándar de nodos visuales para Stable Diffusion, FLUX y modelos de vídeo (AnimateDiff, Stable Video Diffusion). Máximo control y cero costes por API.
- **Stable Diffusion WebUI (AUTOMATIC1111 / Forge):** La interfaz clásica optimizada para generación local de imágenes y control de flujos estáticos.
- **Fooocus:** Interfaz simplificada (estilo Midjourney) diseñada para ejecutar FLUX y SDXL en local con un rendimiento excelente y sin complicaciones de nodos.
- **Ollama + AnythingLLM / Interfaces Locales:** Para procesamiento multimedia auxiliar y control por texto de scripts locales.

---

## 4. Plugins de Generación de Vídeo por Código & Agentes

Plugins, extensiones y adaptadores diseñados para que agentes de IA programen y rendericen vídeo de manera programática.

- **Remotion Video Plugin for DeepSeek Harness (`chenjie1129/remotion-video-plugin`):**
  - **Qué hace:** Permite a agentes autónomos (como los de DeepSeek Harness) crear, previsualizar y renderizar vídeos basados en código React (Remotion) de forma verificada.
  - **Flujo:** El agente escribe animaciones fotograma a fotograma usando `useCurrentFrame()`, `interpolate()` y componentes de vídeo, revisa las imágenes estáticas resultantes (stills) y exporta un vídeo limpio en H.264 sin dependencias de servicios cloud de pago.
  - **Más info:** [05-desktop-apps/deepseek-harness/plugins/README.md](../05-desktop-apps/deepseek-harness/plugins/README.md)
- **Remotion para Claude (MCP / agentes):** Existen adaptadores y servidores MCP que permiten a Claude Desktop generar y renderizar vídeos con Remotion de forma programática. Ver [05-desktop-apps/claude-desktop/mcp-servers/README.md](../05-desktop-apps/claude-desktop/mcp-servers/README.md).
- **Manim (Mathematical Animation Engine):** Aunque no es un plugin de IA per se, es la librería ideal en Python para que un LLM (como Claude o GPT) genere código matemático y renderice animaciones científicas exactas de alta calidad.

---

## 5. Conectores y APIs de Automatización Multimedia

Librerías, SDKs y wrappers para integrar la generación multimedia dentro de tus propias aplicaciones o scripts de automatización (Python/Node.js).

- **FFmpeg (Python wrapper `ffmpeg-python`):** Imprescindible para cortar, unir, reescalar y post-procesar de forma automatizada cualquier vídeo generado por IA mediante scripts.
- **OpenRouter / Gemini Multimodal Connectors:** Para enviar frames de vídeos a modelos de visión y extraer metadatos, transcripciones o auto-generar prompts descriptivos de vídeo a vídeo.
- **ElevenLabs API SDK:** Integración por código para síntesis de voz ultra realista sincronizada con los vídeos generados.

### Conectores por agente / app de escritorio

Si un conector o plugin multimedia pertenece a un agente o app de escritorio de la lista, se documenta en su sección correspondiente:

- **DeepSeek Harness (plugins):** [05-desktop-apps/deepseek-harness/plugins/README.md](../05-desktop-apps/deepseek-harness/plugins/README.md)
- **DeepSeek Harness (connectors):** [05-desktop-apps/deepseek-harness/connectors/README.md](../05-desktop-apps/deepseek-harness/connectors/README.md)
- **Claude Desktop (MCP servers):** [05-desktop-apps/claude-desktop/mcp-servers/README.md](../05-desktop-apps/claude-desktop/mcp-servers/README.md)
- **ChatGPT (connectors):** [05-desktop-apps/chatgpt/connectors/README.md](../05-desktop-apps/chatgpt/connectors/README.md)
- **ChatGPT (custom GPTs):** [05-desktop-apps/chatgpt/custom-gpts/README.md](../05-desktop-apps/chatgpt/custom-gpts/README.md)
- **Antigravity (plugins):** [05-desktop-apps/antigravity/plugins/README.md](../05-desktop-apps/antigravity/plugins/README.md)
- **Antigravity (skills):** [05-desktop-apps/antigravity/skills/README.md](../05-desktop-apps/antigravity/skills/README.md)
- **Aider:** [03-agentes-y-llms/aider/README.md](../03-agentes-y-llms/aider/README.md)
- **Cline:** [03-agentes-y-llms/cline/README.md](../03-agentes-y-llms/cline/README.md)
- **OpenHands:** [03-agentes-y-llms/openhands/README.md](../03-agentes-y-llms/openhands/README.md)
- **Hermes Agent:** [03-agentes-y-llms/hermes-agent/README.md](../03-agentes-y-llms/hermes-agent/README.md)

---

## Tabla resumen

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Pavo AI | Herramienta web | [app.pavo-ai.work](https://app.pavo-ai.work/) | Generación texto a vídeo e imágenes |
| Kling AI | Vídeo IA | [klingai.com](https://klingai.com/) | Vídeo cinemático, créditos diarios |
| Luma Dream Machine | Vídeo IA | [lumalabs.ai](https://lumalabs.ai/) | Text/image-to-video |
| RunwayML | Vídeo IA | [runwayml.com](https://runwayml.com/) | Gen-3 Alpha, créditos de prueba |
| PixVerse / Hailuo AI | Vídeo IA | [pixverse.ai](https://pixverse.ai/) | Fluidez de movimiento |
| Civitai | Imágenes | [civitai.com](https://civitai.com/) | Modelos open-source, LoRAs |
| Hugging Face Spaces | Imágenes | [huggingface.co/spaces](https://huggingface.co/spaces) | FLUX, SD3 gratuitos |
| Tensor.Art | Imágenes | [tensor.art](https://tensor.art/) | Cuota diaria, LoRAs |
| Leonardo.ai | Imágenes | [leonardo.ai](https://leonardo.ai/) | 150 créditos/día |
| ComfyUI | Local | [github.com/comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI) | Nodos visuales, SD/FLUX/vídeo |
| AUTOMATIC1111 / Forge | Local | [github.com/AUTOMATIC1111/stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui) | Interfaz clásica |
| Fooocus | Local | [github.com/lllyasviel/Fooocus](https://github.com/lllyasviel/Fooocus) | Estilo Midjourney, FLUX/SDXL |
| Remotion Video Plugin | Plugin | [GitHub](https://github.com/chenjie1129/remotion-video-plugin) | Vídeo por código con agentes |
| Manim | Librería | [manim.community](https://www.manim.community/) | Animaciones matemáticas |
| FFmpeg (ffmpeg-python) | Librería | [github.com/kkroening/ffmpeg-python](https://github.com/kkroening/ffmpeg-python) | Post-procesado de vídeo |
| ElevenLabs API SDK | SDK | [elevenlabs.io](https://elevenlabs.io/) | Síntesis de voz |

---

## 6. Más herramientas de imagen y vídeo

### Imagen

- **Midjourney:** Generación de imágenes de alta calidad (de pago, sin tier gratuito permanente; pruebas ocasionales).
- **DALL·E 3 (OpenAI):** Integrado en ChatGPT; tier gratuito limitado.
- **Ideogram:** Generación de imágenes con texto legible; tier gratuito diario.
- **Recraft:** Generación de imágenes y vectores; tier gratuito.
- **Playground AI:** 500 imágenes/día gratis con modelos SD/SDXL.
- **Bing Image Creator (DALL·E 3):** Gratuito con cuenta Microsoft.

### Vídeo

- **Sora (OpenAI):** Generación de vídeo (acceso limitado, de pago).
- **Veo (Google):** Generación de vídeo (acceso limitado).
- **Haiper:** Generación de vídeo gratuita con créditos diarios.
- **Vidu:** Generación de vídeo con tier gratuito.
- **Krea AI:** Generación y edición de imagen/vídeo en tiempo real; tier gratuito.

### Audio / Música

- **Suno:** Canciones completas con voz; tier gratuito (50 créditos/día).
- **Udio:** Música generada por IA; tier gratuito.
- **ElevenLabs:** Voz y SFX; tier gratuito (10k caracteres/mes).
- **Piper (TTS local):** Síntesis de voz local, coste cero.
- **Coqui TTS:** TTS open-source local.

### Edición

- **CapCut Web:** Subtitulado y edición con IA.
- **Descript:** Edición de vídeo por texto; tier gratuito limitado.
- **Clipchamp:** Editor de vídeo web con IA; tier gratuito.

### Tabla adicional

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Ideogram | Imagen | [ideogram.ai](https://ideogram.ai/) | Texto legible en imágenes |
| Recraft | Imagen/Vectores | [recraft.ai](https://www.recraft.ai/) | Vectores e imágenes |
| Playground AI | Imagen | [playgroundai.com](https://playgroundai.com/) | 500 img/día gratis |
| Bing Image Creator | Imagen | [bing.com/images/create](https://www.bing.com/images/create) | DALL·E 3 gratuito |
| Haiper | Vídeo | [haiper.ai](https://haiper.ai/) | Créditos diarios |
| Vidu | Vídeo | [vidu.studio](https://www.vidu.studio/) | Tier gratuito |
| Krea AI | Imagen/Vídeo | [krea.ai](https://www.krea.ai/) | Tiempo real |
| Piper TTS | Audio (local) | [github.com/rhasspy/piper](https://github.com/rhasspy/piper) | TTS local gratuito |
| Coqui TTS | Audio (local) | [github.com/coqui-ai/TTS](https://github.com/coqui-ai/TTS) | TTS open-source |
| Descript | Edición | [descript.com](https://www.descript.com/) | Edición por texto |
| Clipchamp | Edición | [clipchamp.com](https://clipchamp.com/) | Editor web con IA |
