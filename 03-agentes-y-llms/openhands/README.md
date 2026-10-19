# OpenHands (antes OpenDevin)

Framework de agentes de software autónomos.

## Despliegue rápido con Docker

```bash
docker pull docker.all-hands.dev/all-hands-ai/openhands:latest
docker run -it --rm \
  -e SANDBOX_RUNTIME_CONTAINER_IMAGE=docker.all-hands.dev/all-hands-ai/runtime:latest \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -p 3000:3000 \
  docker.all-hands.dev/all-hands-ai/openhands:latest
```

Abre `http://localhost:3000` en el navegador.

## Configuración del modelo backend

Apunta a LLMs locales con Ollama o a APIs externas editando la configuración:

```bash
# Ejemplo: usar Ollama local
export LLM_BASE_URL=http://host.docker.internal:11434/v1
export LLM_MODEL=ollama/llama3.1
```

O configura OpenRouter / OpenAI desde la UI de settings.

## Casos de uso

- Resolver issues de GitHub de forma autónoma.
- Refactorizar repositorios completos.
- Ejecutar tests y corregir errores en bucle.

## Notas

- Requiere Docker para el sandbox de ejecución.
- Ideal para tareas de ingeniería de software end-to-end.
- Soporta navegación web y terminal dentro del sandbox.
