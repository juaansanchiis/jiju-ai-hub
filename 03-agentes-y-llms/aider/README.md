# Aider

Agente de código en terminal basado en LLMs.

## Instalación rápida

```bash
pip install aider-chat
```

## Configuración con APIs baratas o gratuitas

Configura variables de entorno para usar OpenRouter con modelos potentes (incluidos los `:free`):

```bash
export OPENAI_API_BASE=https://openrouter.ai/api/v1
export OPENAI_API_KEY=$OPENROUTER_API_KEY
aider --model openrouter/meta-llama/llama-3.1-70b-instruct
```

### Modelos recomendados

- **Código:** `openrouter/qwen/qwen-2.5-coder-32b-instruct` o `deepseek/deepseek-coder`.
- **Razonamiento:** `openrouter/anthropic/claude-3.5-sonnet` (de pago) o `openrouter/meta-llama/llama-3.1-70b-instruct:free`.
- **Local (Ollama):** `ollama/qwen2.5-coder:7b`.

## Comandos esenciales

- `/add <archivo>` — Añade archivos al contexto.
- `/code <instrucción>` — Pide a la IA que modifique el código.
- `/commit` — Genera un commit con mensaje automático.
- `/diff` — Muestra los cambios pendientes.
- `/undo` — Revierte el último cambio.
- `/test` — Ejecuta tests y corrige errores.
- `/lint` — Ejecuta linters.
- `/map` — Muestra el mapa del repositorio.

## Buenas prácticas

- Usa `--no-auto-commits` si prefieres controlar los commits manualmente.
- Limita el contexto con `.aiderignore`.
- Funciona mejor con modelos con buen soporte de tool calling.

## Notas

- Se integra nativamente con Git (commits automáticos por cambio).
- Soporta múltiples proveedores (OpenAI, Anthropic, OpenRouter, Ollama, etc.).
