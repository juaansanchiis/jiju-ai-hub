# Stagehand

Framework de automatización de navegador nativo para IA construido sobre Playwright. En lugar de selectores CSS frágiles, permite usar lenguaje natural: `page.act("Haz clic en el botón de login")` o `page.extract("Saca todos los precios")`.

- **Tipo:** Framework de automatización web con IA
- **Enlace:** [github.com/browserbase/stagehand](https://github.com/browserbase/stagehand)
- **Licencia:** MIT

## Instalación

```bash
npm install @browserbasehq/stagehand
# o
pip install stagehand
```

## Configuración rápida (TypeScript)

```typescript
import { Stagehand } from "@browserbasehq/stagehand";

const stagehand = new Stagehand({
  env: "LOCAL",
  modelName: "gpt-4o",
});
await stagehand.init();
const page = stagehand.page;

await page.goto("https://example.com");
await page.act("Haz clic en el botón de login");
const data = await page.extract("Extrae el nombre y precio de cada producto");
console.log(data);
await stagehand.close();
```

## Métodos principales

| Método | Descripción |
| --- | --- |
| `page.act(instruction)` | Ejecuta una acción descrita en lenguaje natural |
| `page.extract(instruction, schema)` | Extrae datos estructurados de la página |
| `page.observe(instruction)` | Observa y devuelve posibles acciones |
| `page.goto(url)` | Navega a una URL |

## Casos de uso

- Extracción de datos de sitios sin API.
- Automatización de flujos de login/checkout.
- Testing de UI con instrucciones en lenguaje natural.
- Agentes que interactúan con dashboards web.

## Buenas prácticas

1. Define esquemas Zod/Pydantic para `extract` y reduce alucinaciones.
2. Usa `observe` antes de `act` para validar que la acción es posible.
3. Combina con Browserbase para ejecución en la nube con proxies.
4. Cachea resultados de extracción para ahorrar tokens.

## Troubleshooting

- **Acción no encontrada:** Reformula la instrucción o usa `observe` primero.
- **Timeouts:** Aumenta `timeout` en la config de Stagehand.
- **Modelo no soportado:** Verifica la lista de modelos compatibles en la doc.
