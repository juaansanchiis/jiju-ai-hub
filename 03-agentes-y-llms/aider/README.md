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

## Comandos esenciales

- `/add <archivo>` — Añade archivos al contexto.
- `/code <instrucción>` — Pide a la IA que modifique el código.
- `/commit` — Genera un commit con mensaje automático.
- `/diff` — Muestra los cambios pendientes.
- `/undo` — Revierte el último cambio.

## Notas

- Funciona mejor con modelos con buen soporte de tool calling.
- Usa `--no-auto-commits` si prefieres controlar los commits manualmente.
