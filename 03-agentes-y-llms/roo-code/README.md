# Roo Code (Roo Cline)

Fork de Cline que se ha hecho ultra famoso. Le da mil vueltas al original porque permite cambiar el "rol" del agente (Arquitecto, QA, Creador) y tiene un manejo de herramientas mucho más bestia.

- **Tipo:** Extensión de VS Code (fork de Cline)
- **Enlace:** [github.com/RooVetGit/Roo-Code](https://github.com/RooVetGit/Roo-Code)
- **Licencia:** Apache 2.0

## Instalación

1. Abre VS Code.
2. Ve a Extensions (Ctrl+Shift+X).
3. Busca "Roo Code" e instala.
4. Configura tu proveedor de API (OpenRouter, Anthropic, OpenAI, Ollama, etc.).

## Roles de agente (modos)

| Rol | Descripción |
| --- | --- |
| **Architect** | Diseña la arquitectura y planifica cambios sin tocar código. |
| **Code** | Escribe y modifica código (modo por defecto). |
| **Ask** | Responde preguntas sobre el código sin modificar archivos. |
| **Debug** | Analiza errores y propone correcciones. |
| **Custom** | Define tu propio rol con instrucciones personalizadas. |

## Características clave

- Cambio de rol en caliente (sin perder contexto).
- Manejo avanzado de herramientas (terminal, filesystem, browser).
- Soporte para múltiples proveedores (OpenRouter, Anthropic, OpenAI, Ollama, etc.).
- Modo "auto-approve" configurable por herramienta.
- Integración con MCP (Model Context Protocol).
- Diff viewer integrado para revisar cambios.

## Configuración recomendada

```json
{
  "roo-cline.apiProvider": "openrouter",
  "roo-cline.openRouterModelId": "anthropic/claude-3.5-sonnet",
  "roo-cline.autoApprovalSettings": {
    "enabled": true,
    "actions": {
      "readFiles": true,
      "writeFiles": false,
      "executeCommands": false
    }
  }
}
```

## Casos de uso

- Desarrollo full-stack con cambio de roles (arquitectura → código → debug).
- Refactorización de código con revisión por rol.
- Análisis de codebase sin modificar archivos (modo Ask).
- Automatización de tareas repetitivas con auto-approve.

## Comparación con Cline

| Aspecto | Cline | Roo Code |
| --- | --- | --- |
| Roles de agente | No | Sí (Architect, Code, Ask, Debug, Custom) |
| Auto-approve granular | Básico | Avanzado por herramienta |
| MCP support | Sí | Sí (mejorado) |
| Comunidad | Grande | Creciendo rápido |
| Actualizaciones | Estables | Frecuentes (fork activo) |

## Buenas prácticas

1. Usa el rol Architect antes de hacer cambios grandes.
2. Activa auto-approve solo para lectura; mantén aprobación para escritura/ejecución.
3. Usa modo Ask para explorar codebases desconocidos.
4. Combina con MCP servers para extender capacidades.
5. Revisa siempre los diffs antes de aceptar.

## Troubleshooting

- **Extensión no carga:** Verifica la versión de VS Code (>=1.85).
- **API key inválida:** Revisa la configuración del proveedor.
- **Rol no cambia:** Reinicia la extensión o recarga la ventana.
- **Auto-approve no funciona:** Verifica la configuración JSON.
- **MCP no conecta:** Verifica la ruta del servidor MCP.
