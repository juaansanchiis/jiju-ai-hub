# Ollama

Runtime local para ejecutar LLMs en tu propia máquina con una API compatible con OpenAI. Ideal para privacidad y coste cero.

## Instalación

- **Linux/macOS:** `curl -fsSL https://ollama.com/install.sh | sh`
- **Windows:** descarga el instalador desde [ollama.com](https://ollama.com/).
- **Docker:** `docker run -d -v ollama:/root/.ollama -p 11434:11434 ollama/ollama`

## Uso básico

```bash
# Descargar un modelo
ollama pull llama3.1
ollama pull qwen2.5-coder:7b
ollama pull deepseek-r1:8b

# Ejecutar en terminal
ollama run llama3.1

# Listar modelos instalados
ollama list

# Eliminar un modelo
ollama rm llama3.1
```

## API (compatible OpenAI)

Base URL: `http://localhost:11434/v1`

```bash
curl http://localhost:11434/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model":"llama3.1","messages":[{"role":"user","content":"Hola"}]}'
```

### Con Python

```python
from openai import OpenAI
client = OpenAI(base_url="http://localhost:11434/v1", api_key="ollama")
response = client.chat.completions.create(
    model="llama3.1",
    messages=[{"role": "user", "content": "Hola"}],
)
print(response.choices[0].message.content)
```

## Modelos recomendados

| Tarea | Modelo | Tamaño |
| --- | --- | --- |
| Código | qwen2.5-coder:7b | 4.7 GB |
| Razonamiento | deepseek-r1:8b | 4.9 GB |
| General | llama3.1:8b | 4.7 GB |
| Ligero | phi3:mini | 2.3 GB |

## Integración con herramientas

- **Aider:** `aider --model ollama/qwen2.5-coder:7b`
- **Cline:** selecciona Ollama como proveedor, apunta a `http://localhost:11434`.
- **Continue:** configura Ollama como proveedor OpenAI-compatible.
- **OpenHands:** `export LLM_BASE_URL=http://host.docker.internal:11434/v1`

## Buenas prácticas

- Usa modelos cuantizados (Q4) para menor uso de VRAM.
- Limita el contexto para evitar OOM en GPUs pequeñas.
- Usa `ollama serve` para exponer la API a otros servicios.

## Solución de problemas

- **OOM (Out of Memory):** usa un modelo más pequeño o reduce el contexto.
- **Modelo lento:** verifica que use GPU (nvidia-smi).
- **API no responde:** verifica que `ollama serve` esté corriendo.

## Notas

- Coste cero, privacidad total.
- Requiere GPU para buen rendimiento (CPU es lento).
- Soporta múltiples modelos simultáneamente.
