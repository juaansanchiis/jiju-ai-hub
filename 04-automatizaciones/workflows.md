# Automatizaciones

Flujos, scripts y procesos reutilizables.

## N8N / Flowise / Make

Patrones para montar flujos de automatización locales y gratuitos.

### n8n self-hosted con Docker

```bash
docker run -it --rm \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  n8nio/n8n
```

Abre `http://localhost:5678`. Usa webhooks, cron y nodos de IA para orquestar flujos.

### Flowise

Interfaz visual para chains de LangChain. Despliegue con Docker:

```bash
docker run -d -p 3000:3000 flowiseai/flowise
```

### Make (Integromat)

Alternativa SaaS con tier gratuito; útil para integraciones rápidas sin infraestructura.

## Scripts de Python recurrentes

Pequeños boilerplates para conectar webhooks, procesar JSONs con LLMs y automatizar tareas repetitivas.

### Webhook → LLM → respuesta

```python
import os, json, requests
from http.server import BaseHTTPRequestHandler, HTTPServer

OPENROUTER_KEY = os.environ["OPENROUTER_API_KEY"]

def ask_llm(prompt):
    r = requests.post(
        "https://openrouter.ai/api/v1/chat/completions",
        headers={"Authorization": f"Bearer {OPENROUTER_KEY}"},
        json={"model": "meta-llama/llama-3.1-8b-instruct:free",
              "messages": [{"role": "user", "content": prompt}]},
    )
    return r.json()["choices"][0]["message"]["content"]

class Handler(BaseHTTPRequestHandler):
    def do_POST(self):
        data = json.loads(self.rfile.read(int(self.headers["Content-Length"])))
        reply = ask_llm(data.get("text", ""))
        self.send_response(200)
        self.send_header("Content-Type", "application/json")
        self.end_headers()
        self.wfile.write(json.dumps({"reply": reply}).encode())

HTTPServer(("0.0.0.0", 8080), Handler).serve_forever()
```

### Procesar JSON con LLM

```python
import json, os, requests

def summarize(items):
    prompt = "Resume en 3 bullets:\n" + json.dumps(items, ensure_ascii=False)
    r = requests.post(
        "https://openrouter.ai/api/v1/chat/completions",
        headers={"Authorization": f"Bearer {os.environ['OPENROUTER_API_KEY']}"},
        json={"model": "meta-llama/llama-3.1-8b-instruct:free",
              "messages": [{"role": "user", "content": prompt}]},
    )
    return r.json()["choices"][0]["message"]["content"]
```

## Tabla resumen

| Nombre del flujo | Herramientas | Enlace | Descripción | Estado |
| --- | --- | --- | --- | --- |
| n8n self-hosted | Docker, n8n | [n8n.io](https://n8n.io/) | Automatización local gratuita | Activo |
| Flowise | Docker, Flowise | [flowiseai.com](https://flowiseai.com/) | Chains visuales | Activo |
| Webhook → LLM | Python, OpenRouter | — | Procesamiento de mensajes | Boilerplate |
