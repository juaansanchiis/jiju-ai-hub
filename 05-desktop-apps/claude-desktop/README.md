# Claude Desktop

Configuración del archivo `claude_desktop_config.json` para mapear rutas y herramientas locales.

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

## Secciones

- [MCP Servers](mcp-servers/README.md)
