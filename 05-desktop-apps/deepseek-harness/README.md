# DeepSeek Harness

Configuración para exprimir al máximo los modelos de DeepSeek (tanto vía API como en local si usas versiones destiladas).

## Modelos disponibles

- **DeepSeek-V3:** Modelo general potente y económico. Excelente para código y razonamiento.
- **DeepSeek-R1:** Modelo de razonamiento (chain-of-thought). Ideal para tareas complejas.
- **Versiones destiladas:** Para ejecución local con Ollama (ej. `deepseek-r1:8b`, `deepseek-r1:14b`).

## Uso vía API

```bash
curl https://api.deepseek.com/chat/completions \
  -H "Authorization: Bearer $DEEPSEEK_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"deepseek-chat","messages":[{"role":"user","content":"Hola"}]}'
```

### Con Python (OpenAI-compatible)

```python
from openai import OpenAI
client = OpenAI(api_key=os.getenv("DEEPSEEK_API_KEY"), base_url="https://api.deepseek.com")
response = client.chat.completions.create(
    model="deepseek-chat",
    messages=[{"role": "user", "content": "Hola"}],
)
print(response.choices[0].message.content)
```

## Uso local (destilado)

```bash
ollama pull deepseek-r1:8b
ollama run deepseek-r1:8b
```

## Precios (API)

- **deepseek-chat (V3):** ~$0.27/1M tokens entrada, ~$1.10/1M tokens salida.
- **deepseek-reasoner (R1):** ~$0.55/1M tokens entrada, ~$2.19/1M tokens salida.
- Mucho más barato que GPT-4o o Claude.

## Secciones

- [Plugins](plugins/README.md)
- [Conectores](connectors/README.md)

## Buenas prácticas

- Usa DeepSeek-R1 para razonamiento complejo y V3 para tareas generales.
- Aprovecha el bajo coste para prototipado intensivo.
- Usa versiones destiladas para desarrollo offline.
- Combina con fallback a otros proveedores para alta disponibilidad.

## Solución de problemas

- **Rate limit:** espera o cambia de modelo.
- **Respuestas lentas (R1):** el razonamiento toma tiempo; usa streaming.
- **Modelo local lento:** reduce el tamaño del modelo destilado.

## Notas

- API compatible con OpenAI (fácil integración).
- Excelente relación calidad/precio.
- Modelos open-weight disponibles para self-hosting.
