# APIs y planes gratuitos

Proveedores y límites de uso gratuito para desarrollo y testing sin coste.

## OpenRouter

Aprovecha los modelos gratuitos añadiendo `:free` al ID del modelo (ej. `meta-llama/llama-3.1-8b-instruct:free`). Ideal para desarrollo y testing sin coste. Límites de tasa más bajos que los planes de pago, pero suficientes para prototipado.

```bash
# Ejemplo con curl
curl https://openrouter.ai/api/v1/chat/completions \
  -H "Authorization: Bearer $OPENROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"meta-llama/llama-3.1-8b-instruct:free","messages":[{"role":"user","content":"Hola"}]}'
```

## Google AI Studio (Gemini)

Límites de uso gratuito de la API de Gemini (Flash y Pro). Genera las keys de forma segura desde [aistudio.google.com](https://aistudio.google.com/). No compartas las keys en repositorios; usa variables de entorno.

- **Gemini Flash:** mayor cuota gratuita, ideal para tareas rápidas.
- **Gemini Pro:** cuota más reducida, mejor para razonamiento complejo.

## Groq / Mistral / Cohere

Endpoints gratuitos con límites de tasa (*rate limits*) muy altos para inferencia ultra rápida.

- **Groq:** LPU para inferencia a baja latencia; tier gratuito generoso.
- **Mistral:** Modelos open-weight con API gratuita para pruebas.
- **Cohere:** Tier gratuito para experimentación con Command y Embed.

## Hugging Face Inference API / Serverless

Uso básico de modelos open-source mediante peticiones HTTP. El tier gratuito permite probar modelos sin desplegar infraestructura propia.

```python
import requests
API_URL = "https://api-inference.huggingface.co/models/gpt2"
headers = {"Authorization": "Bearer hf_..."}
response = requests.post(API_URL, headers=headers, json={"inputs": "Hola"})
print(response.json())
```

## Tabla resumen

| Proveedor | Servicio/API | Plan gratuito | Enlace | Notas |
| --- | --- | --- | --- | --- |
| OpenRouter | Chat completions | Modelos `:free` | [openrouter.ai](https://openrouter.ai/) | Rate limits bajos |
| Google AI Studio | Gemini Flash/Pro | Tier gratuito | [aistudio.google.com](https://aistudio.google.com/) | Keys seguras |
| Groq | Inferencia LPU | Tier gratuito | [groq.com](https://groq.com/) | Ultra rápido |
| Mistral | Chat completions | Tier gratuito | [mistral.ai](https://mistral.ai/) | Open-weight |
| Cohere | Command/Embed | Tier gratuito | [cohere.com](https://cohere.com/) | Experimentación |
| Hugging Face | Inference API | Tier gratuito | [huggingface.co](https://huggingface.co/) | Modelos OSS |
