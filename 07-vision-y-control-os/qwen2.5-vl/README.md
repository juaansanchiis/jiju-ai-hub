# Qwen2.5-VL (Local)

El modelo multimodal open-source más potente ahora mismo. Permite analizar vídeos fotograma a fotograma, leer documentos complejos, entender gráficos y controlar interfaces. Guía para correrlo en local.

- **Tipo:** Modelo multimodal (visión + lenguaje)
- **Enlace:** [github.com/QwenLM/Qwen2.5-VL](https://github.com/QwenLM/Qwen2.5-VL)
- **Licencia:** Apache 2.0

## Variantes

| Modelo | Parámetros | VRAM mínima | Uso |
| --- | --- | --- | --- |
| Qwen2.5-VL-3B | 3B | ~6 GB | Ligero, edge devices |
| Qwen2.5-VL-7B | 7B | ~16 GB | Balance calidad/velocidad |
| Qwen2.5-VL-72B | 72B | ~48 GB+ | Máxima calidad |

## Instalación con Ollama

```bash
ollama pull qwen2.5vl:7b
ollama run qwen2.5vl:7b
```

## Instalación con Transformers (Python)

```bash
pip install transformers torch torchvision accelerate qwen-vl-utils
```

```python
from transformers import Qwen2_5_VLForConditionalGeneration, AutoProcessor
from qwen_vl_utils import process_vision_info

model = Qwen2_5_VLForConditionalGeneration.from_pretrained(
    "Qwen/Qwen2.5-VL-7B-Instruct", torch_dtype="auto", device_map="auto"
)
processor = AutoProcessor.from_pretrained("Qwen/Qwen2.5-VL-7B-Instruct")

messages = [
    {"role": "user", "content": [
        {"type": "image", "image": "screenshot.png"},
        {"type": "text", "text": "Describe qué ves en esta imagen y qué botones son clicables."},
    ]},
]
text = processor.apply_chat_template(messages, tokenize=False, add_generation_prompt=True)
image_inputs, video_inputs = process_vision_info(messages)
inputs = processor(text=[text], images=image_inputs, videos=video_inputs, padding=True, return_tensors="pt").to("cuda")
generated_ids = model.generate(**inputs, max_new_tokens=512)
print(processor.batch_decode(generated_ids, skip_special_tokens=True)[0])
```

## Análisis de vídeo fotograma a fotograma

```python
messages = [
    {"role": "user", "content": [
        {"type": "video", "video": "video.mp4", "max_pixels": 360*420, "fps": 1.0},
        {"type": "text", "text": "Resume lo que ocurre en este vídeo segundo a segundo."},
    ]},
]
```

## Casos de uso

- Análisis de documentos complejos (tablas, gráficos, formularios).
- Control de interfaces por visión (combinado con OmniParser).
- Subtitulado y descripción de vídeos.
- Lectura de capturas de pantalla para agentes de navegador.
- OCR avanzado en múltiples idiomas.

## Cuantización para hardware limitado

```bash
# GGUF con llama.cpp
# Descarga Qwen2.5-VL-7B-Instruct-Q4_K_M.gguf
# Ejecuta con llama.cpp server con soporte multimodal
```

## Buenas prácticas

1. Usa `max_pixels` para controlar el coste de tokens en imágenes grandes.
2. Para vídeos largos, extrae fotogramas clave en lugar de procesar todo.
3. Combina con RAG para documentos largos (chunking por página).
4. Usa la variante 7B para la mayoría de casos; 72B solo si necesitas máxima calidad.

## Troubleshooting

- **CUDA out of memory:** Reduce `max_pixels` o usa cuantización Q4.
- **Lentitud en CPU:** Usa Ollama con aceleración Metal/CUDA o reduce a 3B.
- **Texto ilegible:** Aumenta la resolución de la imagen de entrada.
- **Alucinaciones en vídeo:** Reduce FPS y procesa fotogramas clave.
