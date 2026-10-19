# Cline (antes Claude Dev)

Agente de código para VS Code.

## Configuración de la extensión

1. Instala la extensión **Cline** desde el marketplace de VS Code.
2. Abre el panel de Cline y configura el proveedor de API.

## Conexión a proveedores alternativos o modelos locales

Para ahorrar costes, conecta Cline a OpenRouter o a modelos locales vía Ollama:

- **OpenRouter:** selecciona "OpenRouter" como proveedor e introduce tu API key.
- **Ollama (local):** selecciona "Ollama" y apunta a `http://localhost:11434`.

## Buenas prácticas de permisos

- Revisa cada acción antes de aprobarla (modo "Ask" por defecto).
- Limita el acceso a carpetas sensibles mediante `.clineignore`.
- No otorgues permisos de ejecución de comandos destructivos sin revisión.
- Usa workspaces aislados para experimentos.

## Notas

- Soporta múltiples proveedores y modelos.
- Ideal para desarrollo iterativo con control humano.
