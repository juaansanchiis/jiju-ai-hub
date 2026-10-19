# Browser-use

Agente de navegador open-source que permite a un LLM controlar un navegador real: abrir pestañas, leer el DOM, hacer clics, rellenar formularios y ejecutar flujos web completos a partir de instrucciones en lenguaje natural.

- **Tipo:** Agente de navegador / framework
- **Enlace:** [github.com/browser-use/browser-use](https://github.com/browser-use/browser-use)
- **Licencia:** MIT

## Instalación

```bash
pip install browser-use
playwright install chromium
```

## Configuración rápida

```python
from browser_use import Agent
from langchain_openai import ChatOpenAI

agent = Agent(
    task="Busca un vuelo de Madrid a Tokio para la próxima semana y dime el precio más barato",
    llm=ChatOpenAI(model="gpt-4o"),
)
import asyncio
asyncio.run(agent.run())
```

## Variables de entorno

```bash
export OPENAI_API_KEY="sk-..."
# o usa OpenRouter / modelos locales vía LangChain
```

## Casos de uso

- Reserva de vuelos, hoteles y restaurantes.
- Scraping de sitios dinámicos (SPA) que no exponen API.
- Rellenado automático de formularios y trámites.
- Testing de UI end-to-end con lenguaje natural.
- Monitorización de precios y disponibilidad.

## Modelos recomendados

| Modelo | Proveedor | Notas |
| --- | --- | --- |
| GPT-4o | OpenAI | Mejor seguimiento de instrucciones visuales |
| Claude 3.5 Sonnet | Anthropic | Excelente razonamiento sobre DOM |
| Qwen2.5-VL | Local (Ollama) | Opción gratuita/local con visión |
| Gemini 2.0 Flash | Google | Rápido y barato para tareas simples |

## Buenas prácticas

1. Usa un perfil de navegador aislado (no tu sesión personal).
2. Limita el número de pasos (`max_steps`) para evitar bucles.
3. Activa `headless=False` para depurar visualmente.
4. Guarda capturas de pantalla en cada paso para auditoría.
5. No envíes credenciales reales; usa cuentas de prueba.

## Troubleshooting

- **El agente se queda en bucle:** Reduce la complejidad de la tarea o cambia de modelo.
- **Selectores no encontrados:** Asegúrate de que Playwright está instalado (`playwright install`).
- **Rate limits:** Usa un proveedor con cuota generosa o modelo local.
- **Página no carga:** Añade `wait_for_network_idle` o aumenta timeouts.
