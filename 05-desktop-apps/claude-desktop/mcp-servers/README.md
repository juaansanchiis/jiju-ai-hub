# MCP Servers para Claude Desktop

**Model Context Protocol (MCP):** Configuración de servidores locales imprescindibles para conectar Claude Desktop a tus archivos y terminal local gratis.

## Servidores imprescindibles

- **filesystem:** Acceso a archivos y carpetas locales.
- **git:** Operaciones sobre repositorios Git.
- **fetch:** Peticiones HTTP a APIs externas.
- **sqlite:** Consultas a bases de datos SQLite locales.

## Remotion para Claude (generación de vídeo por código)

Existen adaptadores y servidores MCP que permiten a Claude Desktop generar y renderizar vídeos con Remotion de forma programática (similar al plugin de DeepSeek Harness). Busca servidores MCP de Remotion en el registro de MCP o en GitHub para integrarlos en `claude_desktop_config.json`.

## Instalación

```bash
npm install -g @modelcontextprotocol/server-filesystem @modelcontextprotocol/server-git @modelcontextprotocol/server-fetch
```

## Configuración ejemplo

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "C:\\ruta\\a\\proyectos"]
    },
    "git": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-git"]
    },
    "fetch": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-fetch"]
    },
    "sqlite": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sqlite", "--db-path", "C:\\ruta\\a\\db.sqlite"]
    }
  }
}
```

## Notas

- Reinicia Claude Desktop tras modificar la configuración.
- Limita las rutas expuestas al mínimo necesario.
- Los servidores MCP se ejecutan localmente; sin coste adicional.
