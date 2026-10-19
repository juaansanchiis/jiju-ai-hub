# Claude Desktop

Configuración del archivo `claude_desktop_config.json` para mapear rutas y herramientas locales.

## Instalación

Descarga desde [claude.ai/download](https://claude.ai/download) (Windows/macOS).

## Ubicación del archivo de configuración

- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`
- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`

## Ejemplo de configuración

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "C:\\Users\\tu-usuario\\proyectos"]
    },
    "git": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-git", "--repository", "C:\\Users\\tu-usuario\\proyectos\\repo"]
    }
  }
}
```

## Modelos disponibles

- **Claude 3.5 Sonnet:** Mejor balance calidad/velocidad.
- **Claude 3 Opus:** Máxima capacidad (más lento).
- **Claude 3 Haiku:** Rápido y económico.

## Secciones

- [MCP Servers](mcp-servers/README.md)

## Buenas prácticas

- Limita las rutas expuestas al mínimo necesario.
- Reinicia Claude Desktop tras modificar la configuración.
- Usa variables de entorno para secretos.
- Revisa los permisos de cada servidor MCP.

## Solución de problemas

- **Config no se carga:** verifica la sintaxis JSON.
- **Servidor MCP no arranca:** revisa la instalación de Node.js.
- **Claude no ve las tools:** reinicia la app.

## Notas

- Soporta MCP (Model Context Protocol) para herramientas locales.
- Ideal para desarrollo con acceso a archivos y terminal.
- Los servidores MCP se ejecutan localmente.
