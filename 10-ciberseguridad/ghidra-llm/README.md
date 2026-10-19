# Ghidra + LLM (GPT-WPRE / Ghidrathon)

Scripts que cogen código ensamblador (Assembly) descompilado en Ghidra, se lo pasan a un LLM local y te devuelven una función en C o C++ comentada explicando qué hace ese malware o binario.

- **Tipo:** Plugin de reverse engineering con IA
- **Enlace:** [github.com/NationalSecurityAgency/ghidra](https://github.com/NationalSecurityAgency/ghidra)
- **Licencia:** Apache 2.0 (Ghidra) / MIT (plugins)

## Componentes

| Componente | Descripción |
| --- | --- |
| Ghidra | Desensamblador/decompilador open-source de la NSA |
| Ghidrathon | Ejecuta Python 3 en Ghidra para automatizar análisis |
| GPT-WPRE | Plugin que usa LLMs para renombrar y comentar funciones |
| LLM local (Ollama) | Modelo que analiza el código descompilado |

## Instalación de Ghidra

```bash
# Descarga desde https://ghidra-sre.org/
# Requiere JDK 17+
java -version
# Ejecuta ghidraRun.bat (Windows) o ghidraRun (Linux/macOS)
```

## Instalación de Ghidrathon

```bash
# En Ghidra: File → Install Extensions → Ghidrathon
# O manualmente:
git clone https://github.com/mandiant/Ghidrathon.git
# Copia a <ghidra>/Extensions/Ghidra/
```

## Instalación de GPT-WPRE

```bash
git clone https://github.com/0x6d69636b/GPT-WPRE.git
# Copia el plugin a <ghidra>/Extensions/Ghidra/
# Configura la API key del LLM en las opciones del plugin
```

## Flujo de trabajo

1. Abre un binario en Ghidra y ejecuta el análisis automático.
2. Selecciona una función en el decompilador.
3. Ejecuta el plugin GPT-WPRE → envía el pseudocódigo C al LLM.
4. El LLM devuelve la función renombrada y comentada.
5. Revisa y valida manualmente el resultado.

## Configuración con LLM local (Ollama)

```python
# En Ghidrathon, script Python:
import requests

def ask_llm(code):
    response = requests.post("http://localhost:11434/api/generate", json={
        "model": "qwen2.5-coder:7b",
        "prompt": f"Analiza este código C descompilado y explica qué hace:\n{code}",
        "stream": False,
    })
    return response.json()["response"]
```

## Casos de uso

- Análisis de malware (entender qué hace un binario malicioso).
- Reverse engineering de software propietario.
- Auditoría de seguridad de firmware.
- CTF (Capture The Flag) challenges.
- Análisis de vulnerabilidades en binarios.

## Modelos recomendados

| Modelo | Uso |
| --- | --- |
| Qwen2.5-Coder 7B | Análisis de código descompilado |
| DeepSeek-Coder | Alternativa potente para código |
| CodeLlama | Modelo especializado en código |
| GPT-4o | Máxima calidad (API de pago) |

## Buenas prácticas

1. Usa modelos locales para no enviar binarios a terceros.
2. Valida siempre el resultado del LLM (puede alucinar).
3. Combina análisis estático (Ghidra) con dinámico (debugger).
4. Documenta cada función analizada.
5. Usa nombres descriptivos para funciones y variables.

## Troubleshooting

- **Plugin no carga:** Verifica la versión de Ghidra y JDK.
- **LLM no responde:** Verifica que Ollama está corriendo.
- **Código ilegible:** Aumenta el nivel de optimización del decompilador.
- **Alucinaciones:** Usa modelos más potentes o reduce el tamaño del fragmento.
- **Memoria insuficiente:** Usa modelos cuantizados (Q4).
