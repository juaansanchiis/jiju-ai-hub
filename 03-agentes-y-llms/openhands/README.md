# OpenHands (antes OpenDevin)

Framework de agentes de software autónomos desplegable en Docker.

## Requisitos

- Docker instalado y en ejecución.
- Al menos 4 GB de RAM disponibles.
- API key de un proveedor LLM (o Ollama local).

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

### Ollama (local)

```bash
export LLM_BASE_URL=http://host.docker.internal:11434/v1
export LLM_MODEL=ollama/llama3.1
```

### OpenRouter / OpenAI

Configura desde la UI de settings: proveedor, API key y modelo.

## Casos de uso

- Resolver issues de GitHub de forma autónoma.
- Refactorizar repositorios completos.
- Ejecutar tests y corregir errores en bucle.
- Navegación web para investigación.

## Buenas prácticas

- Limita las iteraciones (max steps) para evitar bucles.
- Usa sandbox aislado (Docker) para seguridad.
- Revisa los cambios antes de hacer merge.

## Solución de problemas

- **Docker no arranca:** verifica que el daemon esté activo.
- **Modelo no responde:** revisa la API key y la URL base.
- **Sandbox lento:** asigna más recursos a Docker.

## Notas

- Requiere Docker para el sandbox de ejecución.
- Ideal para tareas de ingeniería de software end-to-end.
- Soporta navegación web y terminal dentro del sandbox.
