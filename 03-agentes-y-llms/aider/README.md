# Aider

Agente de código en terminal basado en LLMs, integrado nativamente con Git.

## Instalación

```bash
pip install aider-chat
# o con uv
uv tool install aider-chat
```

## Configuración con APIs baratas o gratuitas

### OpenRouter (modelos `:free`)

```bash
export OPENAI_API_BASE=https://openrouter.ai/api/v1
export OPENAI_API_KEY=$OPENROUTER_API_KEY
aider --model openrouter/meta-llama/llama-3.1-70b-instruct
```

### Ollama (local, coste cero)

```bash
ollama pull qwen2.5-coder:7b
aider --model ollama/qwen2.5-coder:7b
```

### Anthropic / OpenAI

```bash
export ANTHROPIC_API_KEY=sk-ant-...
aider --model claude-3-5-sonnet-20241022
```

## Modelos recomendados

| Tarea | Modelo | Proveedor |
| --- | --- | --- |
| Código general | Qwen 2.5 Coder 32B | OpenRouter |
| Razonamiento | Claude 3.5 Sonnet | Anthropic |
| Económico | Llama 3.1 70B :free | OpenRouter |
| Local | Qwen 2.5 Coder 7B | Ollama |

## Comandos esenciales

- `/add <archivo>` — Añade archivos al contexto.
- `/drop <archivo>` — Quita archivos del contexto.
- `/code <instrucción>` — Pide a la IA que modifique el código.
- `/ask <pregunta>` — Pregunta sin modificar código.
- `/commit` — Genera un commit con mensaje automático.
- `/diff` — Muestra los cambios pendientes.
- `/undo` — Revierte el último cambio.
- `/test` — Ejecuta tests y corrige errores.
- `/lint` — Ejecuta linters.
- `/map` — Muestra el mapa del repositorio.
- `/run <cmd>` — Ejecuta un comando en la terminal.

## Buenas prácticas

- Usa `--no-auto-commits` si prefieres controlar los commits manualmente.
- Limita el contexto con `.aiderignore`.
- Usa `--architect` para separar razonamiento (modelo caro) de edición (modelo barato).
- Funciona mejor con modelos con buen soporte de tool calling.

## Solución de problemas

- **Rate limit 429:** cambia de modelo o proveedor; usa `--model` con un `:free` alternativo.
- **Contexto demasiado grande:** usa `/drop` para quitar archivos no relevantes.
- **Commits no deseados:** usa `--no-auto-commits` y revisa con `/diff`.

## Notas

- Se integra nativamente con Git (commits automáticos por cambio).
- Soporta múltiples proveedores (OpenAI, Anthropic, OpenRouter, Ollama, etc.).
- Ideal para desarrollo en terminal y CI/CD.
