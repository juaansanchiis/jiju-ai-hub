# Jan

Cliente de escritorio open-source para LLMs locales. Alternativa a ChatGPT/Claude con enfoque en privacidad.

## Instalación

Descarga desde [jan.ai](https://jan.ai/) (Windows/macOS/Linux).

## Características

- Chat con modelos locales (Llama, Mistral, etc.).
- Descarga de modelos desde el hub integrado.
- API local compatible con OpenAI.
- Soporte de extensiones (plugins).
- RAG integrado (importar documentos).
- Sin telemetría, privacidad total.

## Uso básico

1. Abre Jan.
2. Ve a "Models" y descarga un modelo.
3. Inicia un chat con el modelo.
4. (Opcional) Activa el servidor API en settings.

## API (compatible OpenAI)

Base URL: `http://localhost:1337/v1` (cuando el servidor está activo).

```bash
curl http://localhost:1337/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model":"llama3.1-8b","messages":[{"role":"user","content":"Hola"}]}'
```

## Integración con herramientas

- **Aider:** `aider --model openai/llama3.1-8b --openai-api-base http://localhost:1337/v1`
- **Cline:** selecciona "OpenAI-compatible", apunta a `http://localhost:1337/v1`.

## Buenas prácticas

- Usa modelos cuantizados para mejor rendimiento.
- Activa RAG para consultas sobre documentos propios.
- Mantén Jan actualizado para mejoras de rendimiento.

## Solución de problemas

- **Modelo no descarga:** verifica la conexión a internet.
- **Chat lento:** reduce el contexto o usa un modelo más pequeño.
- **Servidor API no responde:** activa el servidor en settings.

## Notas

- Open-source y gratuito.
- Enfoque en privacidad (sin telemetría).
- Soporta extensiones para ampliar funcionalidad.
