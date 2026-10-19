# 🎙️ Agentes de Voz en Tiempo Real (WebRTC)

Interactuar hablando con latencia de milisegundos, como si fuera una llamada de teléfono. Infraestructura open-source para montar llamadas de voz o vídeo con IA: STT local (Whisper), LLM (Llama 3), TTS (ElevenLabs).

## Tabla de contenidos

- [LiveKit Agents](livekit/README.md)

## Herramientas principales

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| LiveKit Agents | Framework de agentes de voz/vídeo | [github.com/livekit/agents](https://github.com/livekit/agents) | Infraestructura open-source para llamadas de voz/vídeo con IA. STT local (Whisper) + LLM + TTS. |
| Llama 3.1 8B (Audio) | Modelo omni-modal | [huggingface.co/meta-llama](https://huggingface.co/meta-llama) | Configurar el modelo para que escuche directamente el espectrograma de audio (omni-modalidad local). |

## Otras herramientas relacionadas

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Whisper (OpenAI) | STT local | [github.com/openai/whisper](https://github.com/openai/whisper) | Speech-to-Text open-source; corre en local con GPU/CPU. |
| faster-whisper | STT optimizado | [github.com/SYSTRAN/faster-whisper](https://github.com/SYSTRAN/faster-whisper) | Versión optimizada de Whisper con CTranslate2 (más rápido). |
| WhisperX | STT con diarización | [github.com/m-bain/whisperX](https://github.com/m-bain/whisperX) | Whisper + alineación de palabras + diarización de hablantes. |
| ElevenLabs | TTS premium | [elevenlabs.io](https://elevenlabs.io/) | Síntesis de voz ultra realista; tier gratuito mensual. |
| Coqui TTS | TTS open-source | [github.com/coqui-ai/TTS](https://github.com/coqui-ai/TTS) | TTS open-source con clonación de voz. |
| Piper | TTS ligero | [github.com/rhasspy/piper](https://github.com/rhasspy/piper) | TTS rápido y ligero para edge devices. |
| Vosk | STT offline | [alphacephei.com/vosk](https://alphacephei.com/vosk/) | STT offline ligero para dispositivos embebidos. |
| Deepgram | STT en la nube | [deepgram.com](https://deepgram.com/) | STT de baja latencia con tier gratuito. |
| AssemblyAI | STT en la nube | [assemblyai.com](https://www.assemblyai.com/) | STT con análisis de audio y tier gratuito. |
| Pipecat | Framework de voz IA | [github.com/pipecat-ai/pipecat](https://github.com/pipecat-ai/pipecat) | Framework para construir agentes de voz en tiempo real. |
| Vapi | Plataforma de voz IA | [vapi.ai](https://vapi.ai/) | Plataforma para agentes de voz por teléfono (API). |
| Retell AI | Plataforma de voz IA | [retellai.com](https://www.retellai.com/) | Agentes de voz para llamadas telefónicas. |

## Arquitectura típica de un agente de voz

```
Micrófono → STT (Whisper) → LLM (Llama 3) → TTS (ElevenLabs/Piper) → Altavoz
                ↑                                                          ↓
            WebRTC (LiveKit) ←──────────────────────────────────────────────┘
```

## Buenas prácticas

1. Usa STT local (Whisper/faster-whisper) para privacidad y baja latencia.
2. Usa TTS local (Piper/Coqui) para evitar costes y latencia de red.
3. Implementa VAD (Voice Activity Detection) para detectar cuándo el usuario habla.
4. Añade interrupciones (barge-in) para conversaciones naturales.
5. Usa WebRTC (LiveKit) para baja latencia (<200ms).
6. Cachea respuestas frecuentes para reducir latencia del LLM.
