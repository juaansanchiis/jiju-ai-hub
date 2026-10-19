# 🌐 Agentes de Navegación Autónoma (Browser Control)

Herramientas que le dan un navegador web al LLM para que interactúe con páginas reales: scrapear, rellenar formularios, comprar, reservar, automatizar flujos web sin APIs.

## Tabla de contenidos

- [Browser-use](browser-use/README.md)
- [Stagehand](stagehand/README.md)
- [Crawl4AI](crawl4ai/README.md)

## Herramientas principales

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Browser-use | Agente de navegador open-source | [github.com/browser-use/browser-use](https://github.com/browser-use/browser-use) | Le dices "búscame un vuelo a Japón y resérvalo" y el agente abre pestañas, lee el DOM y hace clics por ti. |
| Stagehand | Framework Playwright nativo para IA | [github.com/browserbase/stagehand](https://github.com/browserbase/stagehand) | En lugar de selectores CSS frágiles, usas `page.act("Haz clic en login")` o `page.extract("Saca los precios")`. |
| Crawl4AI | Scraper optimizado para IA | [github.com/unclecode/crawl4ai](https://github.com/unclecode/crawl4ai) | Descarga webs enteras, salta captchas y devuelve Markdown limpio ideal para RAG. |

## Otras herramientas relacionadas

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Playwright | Automatización de navegador | [playwright.dev](https://playwright.dev/) | Base de muchos agentes de navegador; controla Chromium/Firefox/WebKit. |
| Selenium | Automatización clásica | [selenium.dev](https://www.selenium.dev/) | Estándar histórico para control de navegadores; útil con agentes legacy. |
| Puppeteer | Control de Chrome/Chromium | [pptr.dev](https://pptr.dev/) | Librería Node.js para automatizar Chrome; base de muchos scrapers. |
| Skyvern | Agente de navegador con visión | [github.com/Skyvern-AI/skyvern](https://github.com/Skyvern-AI/skyvern) | Usa visión por computador + LLM para automatizar flujos web complejos. |
| LaVague | Framework de agentes web | [github.com/lavague-ai/LaVague](https://github.com/lavague-ai/LaVague) | Convierte instrucciones en lenguaje natural en acciones de navegador. |
| MultiOn | Agente de navegador comercial | [multion.ai](https://www.multion.ai/) | Agente que navega y ejecuta tareas web por ti (API de pago). |
| AgentQL | Lenguaje de consulta para webs | [agentql.com](https://www.agentql.com/) | Consulta elementos de una web con lenguaje natural en lugar de selectores. |
| Firecrawl | Scraper para IA | [firecrawl.dev](https://www.firecrawl.dev/) | Convierte webs en Markdown/JSON limpio; API con tier gratuito. |
| Jina Reader | Lector de URLs para LLMs | [jina.ai/reader](https://jina.ai/reader/) | Prefija `r.jina.ai/` a cualquier URL y obtén Markdown limpio. |
| Apify | Plataforma de scraping | [apify.com](https://apify.com/) | Actores de scraping listos; tier gratuito generoso. |

## Buenas prácticas

1. **Sandboxing:** Ejecuta los agentes de navegador en contenedores o perfiles aislados para no exponer tus cookies/sesiones reales.
2. **Rate limiting:** Respeta los términos de servicio de los sitios; añade delays y rotación de IPs si es necesario.
3. **Extracción estructurada:** Prefiere `page.extract()` / esquemas JSON sobre scraping de texto libre para reducir alucinaciones.
4. **Captchas:** Usa servicios legales (2Captcha, CapSolver) solo cuando tengas permiso; mejor evita sitios con captcha agresivo.
5. **Privacidad:** No envíes datos sensibles (credenciales, tarjetas) a agentes de navegador de terceros.
