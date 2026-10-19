# Screenpipe

Esto es puramente cyberpunk. Una app open-source que corre en segundo plano grabando tu pantalla y tu micro 24/7 de forma local. Usa OCR y STT para leer todo lo que ves. Luego le puedes preguntar a tu IA local: *"¿Qué repo de GitHub estaba mirando ayer por la tarde que tenía un logo rojo?"* y te lo encuentra.

- **Tipo:** Grabación de pantalla/micro para IA (local)
- **Enlace:** [github.com/mediar-ai/screenpipe](https://github.com/mediar-ai/screenpipe)
- **Licencia:** MIT

## Instalación

```bash
# macOS / Linux
curl -fsSL https://raw.githubusercontent.com/mediar-ai/screenpipe/main/install.sh | sh

# Windows: descarga el instalador desde GitHub Releases
```

## Cómo funciona

1. Corre en segundo plano grabando pantalla (OCR) y audio (STT).
2. Indexa todo localmente en una base de datos SQLite + vectorial.
3. Expone una API local para consultar el historial.
4. Se integra con LLMs locales (Ollama) o en la nube.

## Uso básico

```bash
# Iniciar screenpipe
screenpipe

# Consultar vía API
curl http://localhost:3030/search?q=repo+github+logo+rojo
```

## Integración con LLM (Ollama)

```python
import requests

# Buscar en el historial de pantalla
results = requests.get("http://localhost:3030/search", params={"q": "repositorio github"}).json()

# Enviar contexto al LLM
context = "\n".join([r["text"] for r in results["data"]])
response = requests.post("http://localhost:11434/api/generate", json={
    "model": "llama3.1:8b",
    "prompt": f"Basándote en este historial de pantalla:\n{context}\n\nResponde: ¿Qué repo estaba mirando?",
})
print(response.json()["response"])
```

## Características clave

- Grabación 24/7 de pantalla y audio.
- OCR para texto en pantalla.
- STT (Speech-to-Text) para audio.
- Búsqueda semántica sobre el historial.
- 100% local (privacidad total).
- API REST para integración con agentes.

## Casos de uso

- "¿Qué estaba haciendo ayer a las 3pm?"
- "Encuentra el documento que vi la semana pasada con la tabla de precios."
- "¿Qué repo de GitHub tenía un logo rojo?"
- Auditoría personal de productividad.
- Recuperación de información perdida.

## Requisitos

- macOS, Linux o Windows.
- ~2-4 GB RAM para el proceso de grabación.
- GPU opcional para OCR/STT más rápido.

## Buenas prácticas

1. Excluye apps sensibles (banca, contraseñas) de la grabación.
2. Configura la retención de datos (ej. 7 días).
3. Usa en dispositivos personales, no en máquinas compartidas.
4. Monitoriza el uso de disco (la grabación consume espacio).
5. Combina con un LLM local para privacidad total.

## Troubleshooting

- **Alto uso de CPU:** Reduce la frecuencia de captura de pantalla.
- **OCR inexacto:** Aumenta la resolución de captura.
- **STT no reconoce:** Verifica el idioma configurado.
- **Base de datos grande:** Configura retención automática.
- **API no responde:** Verifica que screenpipe está corriendo.
