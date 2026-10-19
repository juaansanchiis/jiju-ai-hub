# llama.cpp

Motor de inferencia en C/C++ para LLMs. Permite cuantizar tus propios modelos (pasar a formato GGUF o EXL2) para que corran a 50 tokens/segundo consumiendo la mitad de RAM. La base de Ollama, LM Studio y muchos otros.

- **Tipo:** Motor de inferencia / cuantización
- **Enlace:** [github.com/ggerganov/llama.cpp](https://github.com/ggerganov/llama.cpp)
- **Licencia:** MIT

## Compilación

```bash
git clone https://github.com/ggerganov/llama.cpp
cd llama.cpp
# CPU
cmake -B build
cmake --build build --config Release
# Con CUDA (NVIDIA)
cmake -B build -DGGML_CUDA=ON
cmake --build build --config Release
# Con Metal (macOS)
cmake -B build -DGGML_METAL=ON
cmake --build build --config Release
```

## Cuantización de un modelo

```bash
# 1. Descarga el modelo en formato Hugging Face (safetensors)
# 2. Convierte a GGUF (FP16)
python convert_hf_to_gguf.py ./modelo-hf --outfile modelo-f16.gguf --outtype f16

# 3. Cuantiza a Q4_K_M
./build/bin/llama-quantize modelo-f16.gguf modelo-q4km.gguf Q4_K_M
```

## Tipos de cuantización

| Tipo | Bits | Calidad | Velocidad | Uso |
| --- | --- | --- | --- | --- |
| Q8_0 | 8 | Excelente | Rápida | GPU con VRAM suficiente |
| Q6_K | 6 | Muy buena | Rápida | Balance calidad/velocidad |
| Q5_K_M | 5 | Buena | Rápida | Recomendado para CPU |
| Q4_K_M | 4 | Buena | Muy rápida | **Recomendado general** |
| Q3_K_M | 3 | Aceptable | Muy rápida | Hardware limitado |
| Q2_K | 2 | Baja | Ultra rápida | Solo para pruebas |

## Ejecución

```bash
# Servidor HTTP (compatible con OpenAI API)
./build/bin/llama-server -m modelo-q4km.gguf --port 8080 -ngl 35

# CLI interactivo
./build/bin/llama-cli -m modelo-q4km.gguf -p "Hola, ¿qué puedes hacer?" -n 256

# Benchmark
./build/bin/llama-bench -m modelo-q4km.gguf
```

## Parámetros clave

| Parámetro | Descripción |
| --- | --- |
| `-m` | Ruta al modelo GGUF |
| `-ngl` | Número de capas en GPU (0 = CPU only) |
| `-c` | Tamaño del contexto (tokens) |
| `-t` | Número de threads (CPU) |
| `--port` | Puerto del servidor HTTP |
| `-n` | Número máximo de tokens a generar |

## Casos de uso

- Correr LLMs en CPU sin GPU.
- Cuantizar modelos propios o fine-tuned.
- Servidor de inferencia local compatible con OpenAI API.
- Edge devices y sistemas embebidos.
- Prototipado rápido sin dependencias pesadas.

## Optimización para i7-14700HX (o similar)

```bash
# Usa todos los cores de rendimiento (P-cores)
./build/bin/llama-server -m modelo-q4km.gguf -t 8 -ngl 0 -c 4096

# Con GPU integrada (Intel Arc)
./build/bin/llama-server -m modelo-q4km.gguf -t 8 -ngl 20 -c 4096
```

## Buenas prácticas

1. Usa Q4_K_M para el mejor balance calidad/velocidad.
2. Ajusta `-t` al número de P-cores de tu CPU.
3. Usa `-ngl` para offload parcial a GPU si tienes VRAM.
4. Reduce `-c` (contexto) si tienes poca RAM.
5. Usa `llama-bench` para medir rendimiento real.
6. Combina con un frontend (KoboldCpp, Open WebUI) para mejor UX.

## Troubleshooting

- **Lentitud:** Reduce threads, usa Q4 en lugar de Q8, o aumenta `-ngl`.
- **OOM (Out of Memory):** Reduce contexto (`-c`) o usa cuantización más agresiva (Q3).
- **Calidad baja:** Usa Q5 o Q6 en lugar de Q4.
- **GPU no detectada:** Recompila con `-DGGML_CUDA=ON` o `-DGGML_METAL=ON`.
- **Modelo no carga:** Verifica que el archivo GGUF es válido y compatible.
