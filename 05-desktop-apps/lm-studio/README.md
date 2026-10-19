# LM Studio

Interfaz gráfica para descargar y servir modelos locales, con servidor OpenAI-compatible. Ideal para usuarios que prefieren GUI sobre CLI.

## Instalación

Descarga desde [lmstudio.ai](https://lmstudio.ai/) (Windows/macOS/Linux).

## Uso básico

1. Abre LM Studio.
2. Busca y descarga un modelo (ej. Llama 3.1, Qwen 2.5 Coder).
3. Ve a la pestaña "Local Server".
4. Inicia el servidor (por defecto en `http://localhost:1234`).

## API (compatible OpenAI)

Base URL: `http://localhost:1234/v1`

```bash
curl http://localhost:1234/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model":"llama-3.1-8b","messages":[{"role":"user","content":"Hola"}]}'
```

### Con Python

```python
from openai import OpenAI
client = OpenAI(base_url="http://localhost:1234/v1", api_key="lm-studio")
response = client.chat.completions.create(
    model="llama-3.1-8b",
    messages=[{"role": "user", "content": "Hola"}],
)
print(response.choices[0].message.content)
```

## Características

- Búsqueda y descarga de modelos desde Hugging Face.
- Chat integrado para probar modelos.
- Servidor local con API OpenAI-compatible.
- Soporte de GPU (CUDA, Metal, Vulkan).
- Cuantización automática.

## Integración con herramientas

- **Aider:** `aider --model openai/llama-3.1-8b --openai-api-base http://localhost:1234/v1`
- **Cline:** selecciona "LM Studio" o "OpenAI-compatible", apunta a `http://localhost:1234/v1`.
- **Continue:** configura LM Studio como proveedor.

## Buenas prácticas

- Descarga modelos cuantizados (Q4/Q5) para menor uso de VRAM.
- Ajusta el contexto según tu GPU.
- Usa el chat integrado para probar antes de integrar.

## Solución de problemas

- **Servidor no arranca:** verifica que el puerto 1234 esté libre.
- **Modelo lento:** reduce el contexto o usa un modelo más pequeño.
- **GPU no detectada:** actualiza drivers o usa CPU.

## Notas

- Interfaz amigable para principiantes.
- Coste cero, privacidad total.
- Soporta múltiples backends (llama.cpp, MLX).
