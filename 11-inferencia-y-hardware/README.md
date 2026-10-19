# ⚙️ Inferencia Extrema y Hardware Embebido

Exprimir al máximo la CPU (como un i7-14700HX) o meter IA en placas pequeñas. Cuantización de modelos, GGUF/EXL2, y micro-LLMs en dispositivos ARM, Raspberry Pi o microcontroladores.

## Tabla de contenidos

- [llama.cpp](llama-cpp/README.md)
- [Micro-LLMs en placas](micro-llms/README.md)

## Herramientas principales

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| llama.cpp | Motor de inferencia en C/C++ | [github.com/ggerganov/llama.cpp](https://github.com/ggerganov/llama.cpp) | Cuantiza tus propios modelos (GGUF/EXL2) para que corran a 50 tokens/segundo consumiendo la mitad de RAM. |
| Micro-LLMs | Modelos diminutos para edge | [huggingface.co](https://huggingface.co/) | Guías para correr Llama-3.2-1B o Qwen-0.5B en Raspberry Pi o Arduino por puerto serie. |

## Otras herramientas relacionadas

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Ollama | Runtime de LLMs local | [ollama.com](https://ollama.com/) | La forma más fácil de correr LLMs en local; usa llama.cpp por debajo. |
| LM Studio | App de escritorio para LLMs | [lmstudio.ai](https://lmstudio.ai/) | Interfaz gráfica para descargar y correr modelos GGUF. |
| vLLM | Motor de inferencia de alto rendimiento | [github.com/vllm-project/vllm](https://github.com/vllm-project/vllm) | Inferencia de alto throughput con PagedAttention; ideal para servidores. |
| TGI (Text Generation Inference) | Servidor de inferencia | [github.com/huggingface/text-generation-inference](https://github.com/huggingface/text-generation-inference) | Servidor de inferencia de Hugging Face con soporte de cuantización. |
| ExLlamaV2 | Motor de inferencia EXL2 | [github.com/turboderp/exllamav2](https://github.com/turboderp/exllamav2) | Inferencia ultra rápida con formato EXL2; mejor que GGUF en GPU. |
| TensorRT-LLM | Inferencia NVIDIA | [github.com/NVIDIA/TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM) | Máximo rendimiento en GPUs NVIDIA. |
| MLC LLM | Compilador de LLMs | [github.com/mlc-ai/mlc-llm](https://github.com/mlc-ai/mlc-llm) | Compila LLMs para móviles, web y edge devices. |
| llamafile | LLM en un solo archivo | [github.com/Mozilla-Ocho/llamafile](https://github.com/Mozilla-Ocho/llamafile) | Empaqueta un LLM en un ejecutable único (Mozilla). |
| KoboldCpp | Frontend para llama.cpp | [github.com/LostRuins/koboldcpp](https://github.com/LostRuins/koboldcpp) | Interfaz web para llama.cpp con funciones avanzadas. |
| Jan | App de escritorio LLM | [jan.ai](https://jan.ai/) | App de escritorio open-source para correr LLMs localmente. |
| GPT4All | App de escritorio LLM | [gpt4all.io](https://gpt4all.io/) | App de escritorio para correr LLMs en CPU. |

## Formatos de cuantización

| Formato | Descripción | Uso |
| --- | --- | --- |
| GGUF | Formato de llama.cpp | CPU/GPU, el más universal |
| EXL2 | Formato de ExLlamaV2 | GPU NVIDIA, máxima velocidad |
| AWQ | Activation-aware Weight Quantization | GPU, buena calidad |
| GPTQ | Post-training quantization | GPU, ampliamente soportado |
| FP16/BF16 | Media precisión | GPU con suficiente VRAM |
| INT8/INT4 | Cuantización entera | Edge devices, CPU |

## Buenas prácticas

1. Usa Q4_K_M para el mejor balance calidad/velocidad en CPU.
2. Usa EXL2 para máxima velocidad en GPU NVIDIA.
3. Cuantiza tus propios modelos con llama.cpp para control total.
4. Usa modelos pequeños (1B-3B) para edge devices.
5. Monitoriza el uso de RAM y VRAM para evitar OOM.
6. Usa `--n-gpu-layers` para offload parcial a GPU.
