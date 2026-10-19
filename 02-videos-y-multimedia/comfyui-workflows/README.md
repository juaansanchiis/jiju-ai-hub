# ComfyUI Workflows

Colección de flujos de trabajo (workflows) para ComfyUI en formato `.json`. Cada archivo se puede cargar directamente en ComfyUI con "Load" y ejecutar.

- **Tipo:** Workflows / plantillas de nodos
- **Enlace:** [github.com/comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI)

## Workflows incluidos

| Archivo | Descripción |
| --- | --- |
| `upscale-supir.json` | Upscale de imágenes con SUPIR (inventa detalles en fotos borrosas). |
| `lcm-realtime.json` | Generación de imágenes en tiempo real con LCM mientras dibujas en un canvas. |
| `text-to-video-svd.json` | Texto a vídeo con Stable Video Diffusion. |
| `flux-txt2img.json` | Generación de imágenes con FLUX.1 [schnell]. |
| `animatediff.json` | Animación de imágenes con AnimateDiff. |

## Cómo usar

1. Abre ComfyUI en tu navegador (`http://127.0.0.1:8188`).
2. Arrastra el archivo `.json` a la ventana o usa "Load" → selecciona el archivo.
3. Ajusta los parámetros (prompt, seed, etc.) y pulsa "Queue Prompt".

## Workflows destacados

### SUPIR Upscale

- **Qué hace:** Toma una imagen de baja resolución y la escala a alta resolución inventando detalles realistas (texturas, pelo, piel).
- **Modelo:** SUPIR (Super-resolution with Image Restoration).
- **VRAM:** ~12 GB (modelo grande).
- **Uso:** Ideal para restaurar fotos antiguas o mejorar renders.

### LCM Real-time

- **Qué hace:** Genera imágenes en tiempo real mientras dibujas en un canvas (Latent Consistency Models).
- **Modelo:** LCM-LoRA sobre SD 1.5 o SDXL.
- **VRAM:** ~6 GB.
- **Uso:** Prototipado rápido, brainstorming visual.

### FLUX.1 [schnell]

- **Qué hace:** Generación de imágenes de alta calidad en 4 pasos.
- **Modelo:** FLUX.1 [schnell] (Apache 2.0).
- **VRAM:** ~12 GB (o ~6 GB con cuantización).
- **Uso:** Generación rápida de conceptos.

## Recursos adicionales

- [ComfyUI Manager](https://github.com/ltdrdata/ComfyUI-Manager) — Instala nodos y modelos fácilmente.
- [ComfyUI Workflows (comunidad)](https://comfyworkflows.com/) — Repositorio de workflows compartidos.
- [OpenArt Workflows](https://openart.ai/workflows) — Workflows listos para usar.

## Buenas prácticas

1. Guarda tus workflows personalizados en esta carpeta para versionarlos.
2. Usa ComfyUI Manager para mantener los nodos actualizados.
3. Documenta los modelos necesarios para cada workflow.
4. Usa seeds fijas para reproducibilidad.
5. Exporta en formato `.json` (no `.png` con metadata) para mejor control de versiones.
