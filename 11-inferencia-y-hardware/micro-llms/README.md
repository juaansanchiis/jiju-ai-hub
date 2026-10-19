# Micro-LLMs en placas (Edge AI)

Guías para correr modelos diminutos (Llama-3.2-1B, Qwen-0.5B, Phi-3-mini) en dispositivos ARM, Raspberry Pi, o integrarlos con microcontroladores (Arduino, ESP32) por puerto serie para hacer robótica con IA.

- **Tipo:** Guía de edge AI / micro-LLMs
- **Enlace:** [huggingface.co](https://huggingface.co/)

## Modelos recomendados para edge

| Modelo | Parámetros | RAM mínima | Dispositivo |
| --- | --- | --- | --- |
| Llama 3.2 1B | 1B | ~1 GB | Raspberry Pi 4/5, móvil |
| Qwen 2.5 0.5B | 0.5B | ~0.5 GB | Raspberry Pi, ESP32 (con cuantización) |
| Phi-3 Mini | 3.8B | ~2.5 GB | Raspberry Pi 5, laptop |
| Gemma 2 2B | 2B | ~1.5 GB | Raspberry Pi 4/5 |
| TinyLlama 1.1B | 1.1B | ~0.8 GB | Raspberry Pi 3/4 |
| SmolLM 1.7B | 1.7B | ~1.2 GB | Raspberry Pi 4/5 |

## Raspberry Pi: instalación con Ollama

```bash
# En Raspberry Pi (ARM64)
curl -fsSL https://ollama.com/install.sh | sh
ollama pull llama3.2:1b
ollama run llama3.2:1b
```

## Raspberry Pi: con llama.cpp

```bash
# Compilar para ARM
git clone https://github.com/ggerganov/llama.cpp
cd llama.cpp
cmake -B build
cmake --build build --config Release -j4

# Descargar modelo GGUF cuantizado
# Ejecutar
./build/bin/llama-cli -m llama-3.2-1b-q4km.gguf -p "Hola" -n 128 -t 4
```

## Integración con Arduino/ESP32 por puerto serie

```python
# Script Python en PC/Raspberry Pi que actúa como puente
import serial
import requests

ser = serial.Serial('/dev/ttyUSB0', 115200)

while True:
    line = ser.readline().decode().strip()
    if line.startswith("PROMPT:"):
        prompt = line[7:]
        response = requests.post("http://localhost:11434/api/generate", json={
            "model": "llama3.2:1b",
            "prompt": prompt,
            "stream": False,
        })
        answer = response.json()["response"]
        ser.write(f"RESPONSE:{answer}\n".encode())
```

```cpp
// Código Arduino/ESP32
void setup() {
  Serial.begin(115200);
}

void loop() {
  Serial.println("PROMPT:¿Qué temperatura hace?");
  delay(5000);
  if (Serial.available()) {
    String response = Serial.readStringUntil('\n');
    Serial.println(response);
  }
}
```

## Casos de uso

- Robótica con IA (control de motores, sensores).
- Asistentes de voz offline en dispositivos portátiles.
- Clasificación de imágenes en edge (con modelos de visión pequeños).
- Automatización del hogar con IA local.
- Dispositivos IoT inteligentes.

## Optimización para edge

1. Usa cuantización Q4 o inferior para reducir RAM.
2. Usa modelos de 1B parámetros o menos.
3. Reduce el contexto (`-c 512` o menos).
4. Usa `mmap` para cargar modelos sin copiar a RAM.
5. Considera MLC LLM para compilación optimizada a ARM.

## Buenas prácticas

1. Prueba primero en PC antes de desplegar en placa.
2. Monitoriza temperatura y consumo de la placa.
3. Usa fuentes de alimentación adecuadas (Raspberry Pi necesita 5V/3A).
4. Implementa fallback si el modelo no responde.
5. Cachea respuestas frecuentes para reducir inferencia.

## Troubleshooting

- **OOM en Raspberry Pi:** Usa modelo más pequeño o cuantización más agresiva.
- **Lentitud extrema:** Reduce contexto, usa menos threads, o cambia a modelo más pequeño.
- **Puerto serie no responde:** Verifica baud rate y conexiones.
- **Modelo no carga:** Verifica arquitectura (ARM64 vs ARM32) y formato GGUF.
- **Sobrecalentamiento:** Añade disipador/ventilador a la placa.
