# LiveKit Agents

Infraestructura open-source para montar llamadas de voz o vídeo con IA. Puedes meterle modelos STT (Speech-to-Text) locales como Whisper, pasarlo por Llama 3, y sacarlo con una voz de ElevenLabs. Latencia de milisegundos vía WebRTC.

- **Tipo:** Framework de agentes de voz/vídeo en tiempo real
- **Enlace:** [github.com/livekit/agents](https://github.com/livekit/agents)
- **Licencia:** Apache 2.0

## Instalación

```bash
pip install livekit-agents livekit-plugins-openai livekit-plugins-silero
# Plugins adicionales
pip install livekit-plugins-deepgram livekit-plugins-elevenlabs livekit-plugins-whisper
```

## Servidor LiveKit (self-hosted)

```bash
# Con Docker
docker run --rm -p 7880:7880 -p 7881:7881 -p 7882:7882/udp \
  livekit/livekit-server --dev
```

## Agente de voz básico (Python)

```python
from livekit.agents import AutoSubscribe, JobContext, WorkerOptions, cli
from livekit.agents.voice_assistant import VoiceAssistant
from livekit.plugins import openai, silero

async def entrypoint(ctx: JobContext):
    await ctx.connect(auto_subscribe=AutoSubscribe.AUDIO_ONLY)
    assistant = VoiceAssistant(
        vad=silero.VAD.load(),
        stt=openai.STT(),
        llm=openai.LLM(model="gpt-4o-mini"),
        tts=openai.TTS(),
    )
    assistant.start(ctx.room)
    await assistant.say("Hola, ¿en qué puedo ayudarte?", allow_interruptions=True)

if __name__ == "__main__":
    cli.run_app(WorkerOptions(entrypoint_fnc=entrypoint))
```

## STT local con Whisper

```python
from livekit.plugins import whisper

stt = whisper.STT(model="base", language="es")
```

## TTS local con Piper

```python
from livekit.plugins import piper

tts = piper.TTS(voice="es_ES-davefx-medium")
```

## LLM local con Ollama

```python
from livekit.plugins import openai

llm = openai.LLM(
    model="llama3.1:8b",
    base_url="http://localhost:11434/v1",
    api_key="ollama",
)
```

## Casos de uso

- Asistentes de voz para atención al cliente.
- Agentes de voz para domótica.
- Tutoriales interactivos por voz.
- Traducción en tiempo real.
- Agentes de voz para juegos.

## Buenas prácticas

1. Usa VAD (Voice Activity Detection) para detectar cuándo el usuario habla.
2. Implementa barge-in (interrupciones) para conversaciones naturales.
3. Usa STT/TTS locales para privacidad y baja latencia.
4. Añade un LLM rápido (modelos pequeños) para reducir latencia.
5. Cachea respuestas frecuentes.
6. Monitoriza la latencia end-to-end (<500ms ideal).

## Troubleshooting

- **Latencia alta:** Usa modelos más pequeños o STT/TTS locales.
- **Audio entrecortado:** Verifica el ancho de banda y la calidad de red.
- **STT no reconoce:** Ajusta el idioma y el modelo de Whisper.
- **TTS robótico:** Usa ElevenLabs o Coqui para voces más naturales.
- **Agente no responde:** Verifica que el servidor LiveKit está corriendo.
