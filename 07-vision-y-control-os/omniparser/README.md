# Microsoft OmniParser

Modelo de visión ligero que coge una captura de tu pantalla, detecta todos los botones, iconos y elementos de UI y los convierte en un JSON estructurado. Se usa para crear agentes que controlan Windows o Linux haciendo clics reales en la interfaz, sin necesidad de APIs.

- **Tipo:** Modelo de visión para UI / agente de control de SO
- **Enlace:** [github.com/microsoft/OmniParser](https://github.com/microsoft/OmniParser)
- **Licencia:** MIT

## Instalación

```bash
git clone https://github.com/microsoft/OmniParser.git
cd OmniParser
pip install -r requirements.txt
```

## Uso básico

```python
from omniparser import OmniParser

parser = OmniParser()
result = parser.parse("screenshot.png")
print(result)  # JSON con elementos detectados: tipo, bbox, texto, interactivo
```

## Salida típica

```json
[
  {"type": "button", "bbox": [120, 340, 200, 380], "text": "Login", "interactive": true},
  {"type": "icon", "bbox": [10, 10, 40, 40], "text": "menu", "interactive": true},
  {"type": "text", "bbox": [50, 50, 300, 80], "text": "Bienvenido", "interactive": false}
]
```

## Integración con agentes

1. Captura la pantalla con `mss` o `pyautogui.screenshot()`.
2. Pasa la imagen a OmniParser → obtén JSON de elementos.
3. Envía el JSON + instrucción al LLM → decide qué elemento clicar.
4. Ejecuta el clic con `pyautogui.click(x, y)`.

## Casos de uso

- Agentes que controlan apps de escritorio sin API.
- Automatización de flujos en apps legacy.
- Testing de UI basado en visión.
- Asistentes de accesibilidad.

## Modelos relacionados

| Modelo | Uso |
| --- | --- |
| OmniParser V2 | Detección de elementos UI (más preciso) |
| YOLO (fine-tuned) | Detección rápida de iconos |
| Grounding DINO | Detección de objetos por texto |

## Buenas prácticas

1. Usa resolución de pantalla consistente para mejorar la detección.
2. Filtra elementos no interactivos antes de enviar al LLM.
3. Añade OCR (Tesseract/EasyOCR) para texto pequeño.
4. Combina con un LLM de razonamiento (GPT-4o, Claude) para decidir acciones.

## Troubleshooting

- **Elementos no detectados:** Aumenta la resolución o usa OmniParser V2.
- **Falsos positivos:** Filtra por confianza mínima (`score > 0.5`).
- **Lentitud:** Usa GPU o reduce el tamaño de la captura.
