# 🖥️ Apps de Escritorio

Introducción al ecosistema de aplicaciones de escritorio orientadas a IA: clientes nativos, wrappers y entornos de ejecución local como LM Studio u Ollama.

---

## Entornos de ejecución local

- **Ollama:** Ejecuta LLMs localmente con una API compatible con OpenAI. Ideal para privacidad y coste cero.
  - Instalación: `curl -fsSL https://ollama.com/install.sh | sh` (Linux/Mac) o descarga el instalador (Windows).
  - Uso: `ollama pull llama3.1`, `ollama run llama3.1`.
  - API: `http://localhost:11434/v1` (compatible OpenAI).
- **LM Studio:** Interfaz gráfica para descargar y servir modelos locales, con servidor OpenAI-compatible.
  - Descarga desde [lmstudio.ai](https://lmstudio.ai/).
  - Servidor local en `http://localhost:1234/v1`.
- **Jan:** Cliente de escritorio open-source para LLMs locales.
- **GPT4All:** Cliente de escritorio para modelos locales con RAG integrado.

## Clientes nativos de IA

- **ChatGPT Desktop:** Cliente oficial de OpenAI con atajos y conectores.
- **Claude Desktop:** Cliente oficial de Anthropic con soporte MCP.
- **DeepSeek:** Acceso vía web/API; clientes de terceros disponibles.

## Tabla resumen

| App | Tipo | Enlace | Notas |
| --- | --- | --- | --- |
| ChatGPT Desktop | Cliente nativo | [openai.com/chatgpt/desktop](https://openai.com/chatgpt/desktop/) | Atajos y conectores |
| Claude Desktop | Cliente nativo | [claude.ai/download](https://claude.ai/download) | Soporte MCP |
| DeepSeek | Cliente/API | [deepseek.com](https://www.deepseek.com/) | Modelos potentes y baratos |
| Ollama | Runtime local | [ollama.com](https://ollama.com/) | LLMs locales, API OpenAI-compatible |
| LM Studio | Runtime local | [lmstudio.ai](https://lmstudio.ai/) | GUI para modelos locales |
| Jan | Cliente local | [jan.ai](https://jan.ai/) | Open-source |
| GPT4All | Cliente local | [gpt4all.io](https://gpt4all.io/) | RAG integrado |
| Antigravity | Entorno propio | — | Documentación interna |

## Índice

- [ChatGPT](chatgpt/README.md)
- [DeepSeek Harness](deepseek-harness/README.md)
- [Claude Desktop](claude-desktop/README.md)
- [Antigravity](antigravity/README.md)
- [Ollama](ollama/README.md)
- [LM Studio](lm-studio/README.md)
- [Jan](jan/README.md)
- [GPT4All](gpt4all/README.md)

