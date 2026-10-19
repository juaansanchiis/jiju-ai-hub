# Conectores de DeepSeek Harness

Enlaces de integración de la API de DeepSeek con herramientas de escritorio o IDEs.

## Integraciones comunes

- **Continue (VS Code/JetBrains):** configura DeepSeek como proveedor OpenAI-compatible.
- **Cline / Aider:** apunta `OPENAI_API_BASE` a `https://api.deepseek.com`.
- **LangChain / LiteLLM:** usa el modelo `deepseek/deepseek-chat`.
- **Cursor:** configura DeepSeek como modelo personalizado.

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
    },
    {
      "title": "DeepSeek Reasoner",
      "provider": "openai",
      "model": "deepseek-reasoner",
      "apiBase": "https://api.deepseek.com",
      "apiKey": "sk-..."
    }
  ]
}
```

## Configuración ejemplo (LiteLLM)

```yaml
model_list:
  - model_name: deepseek-chat
    litellm_params:
      model: deepseek/deepseek-chat
      api_key: os.environ/DEEPSEEK_API_KEY
```

## Buenas prácticas

- Verifica los límites de tasa y costes antes de uso intensivo.
- Usa versiones destiladas para desarrollo offline.
- Combina con fallback a otros proveedores.

## Solución de problemas

- **Conector no aparece:** verifica la configuración JSON.
- **Error de autenticación:** revisa la API key.
- **Modelo no encontrado:** verifica el nombre del modelo.

## Notas

- DeepSeek es compatible con la API de OpenAI.
- Excelente para integración en IDEs y herramientas existentes.
