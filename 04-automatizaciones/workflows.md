# ⚙️ Automatizaciones

Flujos, scripts y procesos reutilizables para automatizar tareas con IA.

---

## 1. Plataformas de Automatización (No-Code / Low-Code)

### n8n (Self-Hosted, gratuito)

La mejor opción para automatización local y gratuita. Soporta webhooks, cron, nodos de IA y más de 400 integraciones.

**Despliegue con Docker:**

```bash
docker run -it --rm \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  n8nio/n8n
```

Abre `http://localhost:5678`. Crea workflows con nodos drag-and-drop.

**Patrones útiles:**
- Webhook → LLM → Respuesta (chatbot).
- Cron → Fetch API → Procesar con LLM → Enviar email/Telegram.
- Trigger de GitHub → Análisis de PR con LLM → Comentario automático.

**Ventajas:** self-hosted, sin límites de ejecuciones, código abierto, nodos de IA nativos (OpenAI, Anthropic, Ollama, Hugging Face).

### Flowise

Interfaz visual para chains de LangChain. Ideal para prototipar RAG y agentes sin código.

```bash
docker run -d -p 3000:3000 flowiseai/flowise
```

**Casos de uso:** chatbots con RAG, agentes con tools, pipelines de documentos.

### Make (Integromat)

Alternativa SaaS con tier gratuito (1000 ops/mes). Útil para integraciones rápidas sin infraestructura.

### Zapier

Tier gratuito (100 tasks/mes). Ideal para conectar apps populares (Gmail, Slack, Notion, etc.) sin código.

### Activepieces

Alternativa open-source a Zapier/Make, self-hostable.

```bash
docker run -d -p 8080:80 activepieces/activepieces
```

---

## 2. Scripts de Python Recurrentes

### Webhook → LLM → Respuesta

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

### Rotación de proveedores (fallback)

```python
import os, requests

PROVIDERS = [
    ("https://openrouter.ai/api/v1", os.getenv("OPENROUTER_API_KEY"), "meta-llama/llama-3.1-8b-instruct:free"),
    ("https://api.groq.com/openai/v1", os.getenv("GROQ_API_KEY"), "llama-3.3-70b-versatile"),
]

def ask_with_fallback(prompt):
    for base_url, api_key, model in PROVIDERS:
        try:
            r = requests.post(
                f"{base_url}/chat/completions",
                headers={"Authorization": f"Bearer {api_key}"},
                json={"model": model, "messages": [{"role": "user", "content": prompt}]},
                timeout=30,
            )
            if r.status_code == 200:
                return r.json()["choices"][0]["message"]["content"]
        except Exception:
            continue
    raise RuntimeError("Todos los proveedores fallaron")
```

### RAG simple con embeddings locales

```python
import os, requests, numpy as np

def embed(text):
    r = requests.post(
        "https://api.openai.com/v1/embeddings",
        headers={"Authorization": f"Bearer {os.getenv('OPENAI_API_KEY')}"},
        json={"model": "text-embedding-3-small", "input": text},
    )
    return np.array(r.json()["data"][0]["embedding"])

def cosine(a, b):
    return np.dot(a, b) / (np.linalg.norm(a) * np.linalg.norm(b))

# Indexar documentos
docs = ["doc1...", "doc2..."]
index = [(d, embed(d)) for d in docs]

def search(query, k=3):
    q = embed(query)
    scored = sorted(index, key=lambda x: cosine(q, x[1]), reverse=True)
    return [d for d, _ in scored[:k]]
```

### Automatización con cron (Linux/WSL)

```bash
# Editar crontab
crontab -e

# Ejecutar script cada hora
0 * * * * /usr/bin/python3 /path/to/script.py >> /path/to/log.txt 2>&1

# Ejecutar cada día a las 9am
0 9 * * * /usr/bin/python3 /path/to/daily.py
```

### Automatización con Task Scheduler (Windows)

```powershell
$action = New-ScheduledTaskAction -Execute "python" -Argument "C:\scripts\daily.py"
$trigger = New-ScheduledTaskTrigger -Daily -At 9am
Register-ScheduledTask -TaskName "DailyAI" -Action $action -Trigger $trigger
```

---

## 3. Patrones de Automatización con LLMs

1. **Clasificación de texto:** Enviar texto a un LLM con prompt de clasificación → guardar resultado en DB.
2. **Extracción de datos:** Prompt con schema JSON → parsear respuesta → validar con Pydantic.
3. **Resumen de documentos:** Chunking → resumen por chunk → resumen final.
4. **Generación de contenido:** Prompt con contexto → generar → revisar → publicar.
5. **Agente con tools:** LLM decide qué tool usar → ejecutar → observar → repetir.

---

## 4. Herramientas complementarias

- **FFmpeg:** Procesamiento de vídeo/audio en scripts.
- **Pandoc:** Conversión de documentos (Markdown ↔ PDF/DOCX).
- **Playwright/Selenium:** Automatización de navegador para scraping.
- **BeautifulSoup:** Parsing de HTML.
- **APScheduler:** Scheduler en Python para tareas recurrentes.
- **Celery + Redis:** Colas de tareas distribuidas.
- **Docker Compose:** Orquestar múltiples servicios (n8n + DB + LLM).

---

## Tabla resumen

| Herramienta | Tipo | Enlace | Descripción | Estado |
| --- | --- | --- | --- | --- |
| n8n | Plataforma | [n8n.io](https://n8n.io/) | Automatización self-hosted | Activo |
| Flowise | Plataforma | [flowiseai.com](https://flowiseai.com/) | Chains visuales LangChain | Activo |
| Make | SaaS | [make.com](https://www.make.com/) | 1000 ops/mes gratis | Activo |
| Zapier | SaaS | [zapier.com](https://zapier.com/) | 100 tasks/mes gratis | Activo |
| Activepieces | Plataforma | [activepieces.com](https://www.activepieces.com/) | Open-source | Activo |
| APScheduler | Librería Python | [apscheduler.readthedocs.io](https://apscheduler.readthedocs.io/) | Scheduler en Python | Activo |
| Celery | Librería Python | [docs.celeryq.dev](https://docs.celeryq.dev/) | Colas distribuidas | Activo |
