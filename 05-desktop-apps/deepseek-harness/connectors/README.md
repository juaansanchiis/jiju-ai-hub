# Conectores de DeepSeek Harness

Enlaces de integración de la API de DeepSeek con herramientas de escritorio o IDEs.

## Integraciones comunes

- **Continue (VS Code/JetBrains):** configura DeepSeek como proveedor OpenAI-compatible.
- **Cline / Aider:** apunta `OPENAI_API_BASE` a `https://api.deepseek.com`.
- **LangChain / LiteLLM:** usa el modelo `deepseek/deepseek-chat`.

## Configuración ejemplo (Continue)

```json
{
  "models": [
    {
      "title": "DeepSeek Chat",
      "provider": "openai",
      "model": "deepseek-chat",
      "apiBase": "https://api.deepseek.com",
      "apiKey": "sk-..."
    }
  ]
}
```

## Notas

- Verifica los límites de tasa y costes antes de uso intensivo.
- Usa versiones destiladas para desarrollo offline.
