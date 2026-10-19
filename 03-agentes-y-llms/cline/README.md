# Cline (antes Claude Dev)

Agente de código para VS Code con permisos avanzados.

## Instalación

1. Abre VS Code.
2. Ve a Extensions (`Ctrl+Shift+X`).
3. Busca **Cline** e instala.
4. Abre el panel de Cline desde la barra lateral.

## Configuración del proveedor

### OpenRouter

- Selecciona "OpenRouter" como proveedor.
- Introduce tu API key de OpenRouter.
- Elige un modelo (ej. `anthropic/claude-3.5-sonnet` o un `:free`).

### Ollama (local, coste cero)

- Selecciona "Ollama" como proveedor.
- Apunta a `http://localhost:11434`.
- Elige un modelo instalado (`ollama list`).

### Anthropic / OpenAI

- Selecciona el proveedor correspondiente e introduce la API key.

## Modelos recomendados

| Tarea | Modelo |
| --- | --- |
| Código | Qwen 2.5 Coder, DeepSeek Coder |
| Razonamiento | Claude 3.5 Sonnet, GPT-4o |
| Económico | Llama 3.1 8B :free |
| Local | Llama 3.1 8B / Qwen 2.5 Coder 7B |

## Buenas prácticas de permisos

- Revisa cada acción antes de aprobarla (modo "Ask" por defecto).
- Limita el acceso a carpetas sensibles mediante `.clineignore`.
- No otorgues permisos de ejecución de comandos destructivos sin revisión.
- Usa workspaces aislados para experimentos.
- Activa "Auto-approve" solo para tareas de bajo riesgo.

## Funcionalidades clave

- Modificación de archivos con diff visual.
- Ejecución de comandos en terminal integrada.
- Navegación web para documentación.
- Creación y edición de archivos múltiples.
- Soporte de MCP (Model Context Protocol) para herramientas externas.

## Solución de problemas

- **Acciones bloqueadas:** revisa los permisos en la configuración de Cline.
- **Modelo no responde:** verifica la API key y el límite de tasa.
- **Contexto grande:** usa `.clineignore` para excluir archivos.

## Notas

- Soporta múltiples proveedores y modelos.
- Ideal para desarrollo iterativo con control humano.
- Puede ejecutar comandos en terminal y modificar archivos con aprobación.
