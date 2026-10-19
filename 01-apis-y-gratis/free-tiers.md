# ⚡ Free Tiers & API Hub

Recopilación de proveedores, modelos y trucos para utilizar APIs de Inteligencia Artificial de forma gratuita o con cuotas muy generosas orientadas al desarrollo, testing y automatización.

---

## 1. OpenRouter (Modelos con `:free`)

OpenRouter mantiene de forma constante un pool de modelos open-source y propietarios que ofrecen coste cero en tokens de entrada y salida (identificados por terminar en `:free`).

- **Cómo usarlo:** Añade `:free` al final del ID del modelo en tus llamadas a la API (por ejemplo, usando librerías compatibles con OpenAI apuntando a la base URL de OpenRouter).
- **Modelos destacados actuales:**
  - **Modelos de Código y Agentes:** Variantes orientadas a desarrollo y terminal (como modelos de la familia Qwen Coder o Poolside).
  - **Razonamiento avanzado:** Modelos de gran tamaño de NVIDIA (como la familia Nemotron Ultra/Super) con contextos masivos de hasta 1M de tokens ideales para RAG y análisis de repositorios enteros.
  - **Multimodal:** Modelos capaces de procesar texto, imagen y vídeo de forma nativa (como variantes de Gemma o Inkling).
  - **El enrutador automático (`openrouter/free`):** Un comodín que redirige automáticamente tu petición al mejor modelo gratuito disponible en ese momento.
- **A tener en cuenta:** Los modelos gratuitos tienen límites de tasa (*rate limits*) dinámicos según la demanda y algunos proveedores pueden aplicar retención de datos si no usas claves con opciones de privacidad estrictas.
- **Límites típicos:** ~20 req/min y ~200 req/día por modelo gratuito (varía por proveedor). Contexto hasta 1M tokens en modelos seleccionados.

---

## 2. Google AI Studio (Gemini API)

La plataforma ideal para desarrolladores que buscan modelos punteros con ventanas de contexto gigantescas.

- **Cuota Gratuita (Free Tier):** Permite utilizar modelos de la familia Flash y versiones seleccionadas de desarrollo a coste cero mediante la interfaz de Google AI Studio o generando una API Key.
- **Límites de Uso:** Se rige por restricciones por minuto (RPM) y por día (RPD). Si excedes las peticiones gratuitas, la API devolverá un error de cuota a menos que vincules una tarjeta de pago (Tier 1).
- **Privacidad en Gratis:** En el nivel gratuito, los datos de las peticiones pueden ser utilizados por Google para mejorar sus productos (puedes desactivarlo habilitando la facturación por consumo).
- **Límites típicos (Free):**
  - Gemini 2.5 Flash: 10 RPM, 250 RPD, 250k TPM.
  - Gemini 2.5 Pro: 5 RPM, 100 RPD, 250k TPM.
  - Contexto: hasta 1M tokens (Flash) / 2M tokens (Pro).
- **Precios (Tier 1, pago por uso):** Flash ~$0.075/1M tokens entrada; Pro ~$1.25/1M tokens entrada.

---

## 3. Proveedores de Alta Velocidad (Groq, Together AI, Mistral)

Alternativas excelentes para integraciones que requieran tiempos de respuesta en milisegundos (inferencia ultra rápida).

- **Groq Cloud:** Ofrece un nivel gratuito muy generoso para modelos open-source (como Llama o Mistral) gracias a su hardware LPU especializado. Ideal para bots de Telegram o scripts rápidos en tiempo real.
  - **Límites Free:** ~30 RPM, ~14.400 RPD (varía por modelo). Modelos: Llama 3.3 70B, Mixtral 8x7B, Gemma 2.
  - **Precios (Developer):** desde $0.05/1M tokens (modelos pequeños) hasta $0.79/1M (70B).
- **Mistral AI La Plateforme:** Ofrece acceso gratuito de prueba a modelos ligeros ideales para clasificación, extracción de datos y tareas lógicas sencillas.
  - **Límites Free:** cuota de prueba limitada; modelos pequeños (Mistral 7B, Mixtral).
  - **Precios (pago):** Mistral Small ~$0.2/1M tokens; Mistral Large ~$2/1M tokens.
- **Hugging Face Serverless Inference API:** Permite lanzar peticiones HTTP directas a miles de modelos alojados en la comunidad sin necesidad de levantar infraestructura propia.
  - **Límites Free:** rate limits por IP/modelo; modelos públicos gratuitos.
  - **Precios (PRO):** $9/mes para mayor cuota y modelos privados.

---

## 4. Otros proveedores gratuitos / generosos

- **Cohere:** Tier gratuito para experimentación con Command y Embed. Límites: ~20 RPM, 1000 llamadas/mes en trial. Precios (Production): Command ~$0.5/1M tokens.
- **Together AI:** Créditos iniciales gratuitos ($1-$25 según promociones) para probar modelos open-source. Precios: desde $0.2/1M tokens.
- **Anthropic (Claude):** Sin tier gratuito permanente; créditos de prueba ocasionales. Precios: Haiku ~$0.25/1M, Sonnet ~$3/1M, Opus ~$15/1M.
- **OpenAI:** Sin tier gratuito permanente; créditos iniciales para cuentas nuevas (variable). Precios: GPT-4o ~$2.5/1M entrada, GPT-4o-mini ~$0.15/1M.

---

## 5. Beneficios para estudiantes (gratis o con descuento)

Varios proveedores ofrecen ventajas a estudiantes verificados (GitHub Student Developer Pack, correo .edu, etc.).

- **GitHub Copilot (Student):** Gratis para estudiantes verificados (GitHub Student Developer Pack). Incluye Copilot en IDEs y Copilot Chat. Sin estudiante: $10/mes (Individual) o $19/mes (Business).
- **Google AI Studio / Gemini (Student):** Los estudiantes suelen tener acceso a cuotas ampliadas y créditos de Google Cloud (hasta $300 en créditos de GCP con verificación .edu). Gemini Advanced gratis 1 año para estudiantes en algunas regiones.
- **JetBrains (Student):** IDEs gratuitos para estudiantes (incluye integración con IA vía AI Assistant con cuota limitada).
- **Azure for Students:** $100 en créditos de Azure sin tarjeta de crédito, incluye acceso a modelos de OpenAI vía Azure OpenAI.
- **AWS Educate / GitHub Student Pack:** Créditos y herramientas gratuitas para estudiantes.
- **Notion / Perplexity / otros:** Perplexity Pro gratis 1 año para estudiantes (verificación .edu). Notion AI con descuentos.

---

## 6. Buenas Prácticas para Automatizaciones con APIs Gratuitas

1. **Rotación de Claves y Fallbacks:** Si construyes scripts o agentes autónomos, programa un sistema de respaldo (*fallback*) que cambie de proveedor gratuito si uno de ellos sufre un corte de tasa (*Rate Limit 429*).
2. **Control de Contexto:** No envíes contextos innecesariamente grandes en modelos gratuitos para evitar agotar el límite de tokens por minuto permitidos.
3. **Cuidado con los Datos Sensibles:** Nunca envíes credenciales, tokens o información privada a endpoints gratuitos de terceros cuyas políticas de privacidad no garanticen la no retención de datos.

---

## Tabla resumen

| Proveedor | Servicio/API | Plan gratuito | Límites típicos | Enlace | Notas |
| --- | --- | --- | --- | --- | --- |
| OpenRouter | Chat completions | Modelos `:free` | ~20 RPM, ~200 RPD | [openrouter.ai](https://openrouter.ai/) | Rate limits dinámicos |
| Google AI Studio | Gemini Flash/Pro | Tier gratuito | Flash 10 RPM/250 RPD; Pro 5 RPM/100 RPD | [aistudio.google.com](https://aistudio.google.com/) | Datos pueden usarse para mejorar productos |
| Groq | Inferencia LPU | Tier gratuito | ~30 RPM, ~14.4k RPD | [groq.com](https://groq.com/) | Ultra rápido |
| Mistral | Chat completions | Prueba gratuita | Cuota limitada | [mistral.ai](https://mistral.ai/) | Modelos ligeros |
| Cohere | Command/Embed | Trial | ~20 RPM, 1000/mes | [cohere.com](https://cohere.com/) | Experimentación |
| Hugging Face | Inference API | Tier gratuito | Rate limits por IP | [huggingface.co](https://huggingface.co/) | Modelos OSS |
| Together AI | Modelos OSS | Créditos iniciales | Variable | [together.ai](https://www.together.ai/) | $1-$25 créditos |
| GitHub Copilot | Asistente de código | Gratis (estudiantes) | Ilimitado (estudiantes) | [github.com/features/copilot](https://github.com/features/copilot) | $10/mes sin estudiante |

---

## 8. Free Tiers ocultos y trucos avanzados

### GitHub Models (Marketplace)

GitHub está regalando acceso gratuito (con rate limits) a modelos premium como **GPT-4o, o1-mini y Llama 3.1** directamente desde su plataforma.

- **Cómo usarlo:** Genera un Personal Access Token (PAT) en GitHub con scope `models:read` y úsalo como API key apuntando a `https://models.inference.ai.azure.com`.
- **Modelos disponibles:** GPT-4o, GPT-4o-mini, o1-mini, o1-preview, Llama 3.1 70B/405B, Mistral Large, Cohere Command R+.
- **Límites Free:** ~150 req/día por modelo (varía), rate limits por minuto. Sin coste.
- **Código (Python, compatible OpenAI):**

```python
from openai import OpenAI
client = OpenAI(
    base_url="https://models.inference.ai.azure.com",
    api_key="ghp_TU_TOKEN_AQUI",
)
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Hola"}],
)
print(response.choices[0].message.content)
```

- **Notas:** Ideal para desarrollo y testing sin coste. Los límites son por usuario/token. No apto para producción de alto volumen.

### Cerebras API (Inferencia ultra rápida)

El hardware más rápido del planeta. Tienen un free tier para desarrolladores donde modelos como Llama 3 vuelan a **~1.000 tokens por segundo**. Es instantáneo.

- **Cómo usarlo:** Regístrate en [cloud.cerebras.ai](https://cloud.cerebras.ai/), genera una API key y usa el endpoint compatible con OpenAI.
- **Modelos disponibles:** Llama 3.1 8B, Llama 3.1 70B, Llama 3.3 70B.
- **Límites Free:** Tier gratuito con rate limits generosos para desarrollo. ~30 RPM, ~1M tokens/día (variable).
- **Velocidad:** ~1.000-2.000 tokens/segundo en modelos 70B (vs ~50-100 en GPU tradicional).
- **Código (Python):**

```python
from openai import OpenAI
client = OpenAI(
    base_url="https://api.cerebras.ai/v1",
    api_key="csk_TU_API_KEY",
)
response = client.chat.completions.create(
    model="llama3.1-70b",
    messages=[{"role": "user", "content": "Hola"}],
)
print(response.choices[0].message.content)
```

- **Notas:** Ideal para agentes que necesitan respuestas instantáneas. La velocidad es su principal ventaja.

### g4f (GPT4Free) — APIs no oficiales

Librerías de Python (`g4f`) que hacen ingeniería inversa a las webs que dan IA gratis y te montan una API falsa en tu PC para que tengas OpenAI o Claude gratis saltándote los bloqueos. Ideal para scripts pequeños.

- **Enlace:** [github.com/xtekky/gpt4free](https://github.com/xtekky/gpt4free)
- **Cómo funciona:** Intercepta las peticiones de las webs gratuitas (ChatGPT web, Claude web, etc.) y las expone como una API compatible con OpenAI en tu máquina.
- **Instalación:**

```bash
pip install -U g4f
```

- **Uso básico:**

```python
import g4f
response = g4f.ChatCompletion.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Hola"}],
)
print(response)
```

- **Proveedores soportados:** OpenAI (web), Anthropic (web), Google (web), Bing, DuckDuckGo, Blackbox, HuggingChat, y muchos más.
- **⚠️ Advertencias:**
  - Viola los términos de servicio de los proveedores.
  - Inestable: los proveedores cambian sus webs y rompen la librería.
  - No apto para producción ni datos sensibles.
  - Úsalo solo para experimentación y scripts personales.
- **Alternativas similares:** `gpt4free` (forks), `freeGPT`, `g4f` con providers de DuckDuckGo/Blackbox.

---

## Tabla resumen actualizada (free tiers ocultos)

| Proveedor | Servicio | Plan gratuito | Límites típicos | Enlace | Notas |
| --- | --- | --- | --- | --- | --- |
| GitHub Models | Modelos premium (GPT-4o, Llama) | Gratis con PAT | ~150 req/día | [github.com/marketplace/models](https://github.com/marketplace/models) | Ideal para dev/testing |
| Cerebras | Inferencia ultra rápida | Tier gratuito | ~30 RPM, ~1M tokens/día | [cerebras.ai](https://www.cerebras.ai/) | ~1000 tokens/s |
| g4f (GPT4Free) | API no oficial | Gratis (ingeniería inversa) | Inestable | [github.com/xtekky/gpt4free](https://github.com/xtekky/gpt4free) | Solo experimentación |

- **Perplexity:** Tier gratuito con límites diarios para búsqueda y chat. Perplexity Pro gratis 1 año para estudiantes (.edu).
- **Fireworks AI:** Créditos iniciales gratuitos para modelos open-source. Precios competitivos.
- **Cerebras:** Inferencia ultra rápida con tier gratuito para modelos seleccionados.
- **SambaNova:** Acceso gratuito a modelos open-source con límites de tasa.
- **Replicate:** Créditos iniciales gratuitos para ejecutar modelos (imagen, vídeo, audio). Pago por segundo de cómputo.
- **Modal:** Créditos gratuitos para serverless GPU. Ideal para desplegar modelos propios.
- **Cloudflare Workers AI:** Tier gratuito generoso para modelos en el edge. Ideal para apps serverless.
- **Vercel AI SDK + proveedores:** Abstracción para cambiar de proveedor fácilmente.

### Tabla adicional

| Proveedor | Servicio | Plan gratuito | Límites típicos | Enlace | Notas |
| --- | --- | --- | --- | --- | --- |
| Perplexity | Búsqueda/Chat | Tier gratuito | Límites diarios | [perplexity.ai](https://www.perplexity.ai/) | Pro gratis para estudiantes |
| Fireworks AI | Modelos OSS | Créditos iniciales | Variable | [fireworks.ai](https://fireworks.ai/) | Rápido y barato |
| Cerebras | Inferencia | Tier gratuito | Límites de tasa | [cerebras.ai](https://www.cerebras.ai/) | Ultra rápido |
| SambaNova | Modelos OSS | Tier gratuito | Límites de tasa | [sambanova.ai](https://sambanova.ai/) | Open-source |
| Replicate | Modelos (img/vid/audio) | Créditos iniciales | Pago por segundo | [replicate.com](https://replicate.com/) | Muchos modelos |
| Modal | Serverless GPU | Créditos gratuitos | Variable | [modal.com](https://modal.com/) | Desplegar modelos propios |
| Cloudflare Workers AI | Modelos en edge | Tier gratuito | Generoso | [developers.cloudflare.com/workers-ai](https://developers.cloudflare.com/workers-ai/) | Serverless |
