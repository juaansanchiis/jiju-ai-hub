# Crawl4AI

El mejor scraper actual para IA. Descarga webs enteras, salta captchas, renderiza JavaScript y devuelve Markdown limpio perfecto para meterlo por RAG a tu modelo local.

- **Tipo:** Scraper / crawler para IA
- **Enlace:** [github.com/unclecode/crawl4ai](https://github.com/unclecode/crawl4ai)
- **Licencia:** Apache 2.0

## Instalación

```bash
pip install crawl4ai
playwright install chromium
```

## Uso básico

```python
import asyncio
from crawl4ai import AsyncWebCrawler

async def main():
    async with AsyncWebCrawler() as crawler:
        result = await crawler.arun(url="https://example.com")
        print(result.markdown)

asyncio.run(main())
```

## Extracción estructurada

```python
from crawl4ai import AsyncWebCrawler, CacheMode
from crawl4ai.extraction_strategy import JsonCssExtractionStrategy

schema = {
    "name": "Productos",
    "baseSelector": "div.product",
    "fields": [
        {"name": "titulo", "selector": "h2", "type": "text"},
        {"name": "precio", "selector": ".price", "type": "text"},
    ],
}
strategy = JsonCssExtractionStrategy(schema)

async with AsyncWebCrawler() as crawler:
    result = await crawler.arun(url="https://tienda.com", extraction_strategy=strategy)
    print(result.extracted_content)
```

## Características clave

- Renderizado completo de JavaScript (SPA).
- Salto de captchas y anti-bot básico.
- Salida en Markdown, HTML o JSON.
- Soporte para crawling profundo (múltiples páginas).
- Integración con LLMs para extracción semántica.
- Cache local para evitar re-descargas.

## Casos de uso

- Alimentar bases de conocimiento RAG con contenido web.
- Monitorización de cambios en sitios.
- Extracción de datos de e-commerce.
- Archivado de documentación técnica.

## Buenas prácticas

1. Respeta `robots.txt` y términos de servicio.
2. Usa delays y concurrencia limitada para no sobrecargar servidores.
3. Cachea resultados para desarrollo iterativo.
4. Filtra contenido irrelevante (nav, footer) antes de enviar al LLM.

## Troubleshooting

- **Página en blanco:** Aumenta `page_timeout` o espera a selectores específicos.
- **Bloqueo anti-bot:** Usa proxies o modo stealth.
- **Memoria alta:** Limita la profundidad de crawling y el número de páginas concurrentes.
