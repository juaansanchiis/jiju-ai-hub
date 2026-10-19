# MCP Servers para Claude Desktop

**Model Context Protocol (MCP):** Configuración de servidores locales imprescindibles para conectar Claude Desktop a tus archivos y terminal local gratis.

## Servidores imprescindibles

- **filesystem:** Acceso a archivos y carpetas locales.
- **git:** Operaciones sobre repositorios Git.
- **fetch:** Peticiones HTTP a APIs externas.
- **sqlite:** Consultas a bases de datos SQLite locales.
- **memory:** Memoria persistente entre conversaciones.
- **sequential-thinking:** Razonamiento paso a paso.

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
    },
    "memory": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"]
    }
  }
}
```

## Otros servidores MCP útiles

- **brave-search:** Búsqueda web con Brave.
- **puppeteer:** Automatización de navegador.
- **slack:** Integración con Slack.
- **google-drive:** Acceso a Google Drive.
- **postgres:** Consultas a PostgreSQL.

## Buenas prácticas

- Reinicia Claude Desktop tras modificar la configuración.
- Limita las rutas expuestas al mínimo necesario.
- Los servidores MCP se ejecutan localmente; sin coste adicional.
- Usa variables de entorno para secretos.

## Solución de problemas

- **Servidor no arranca:** verifica Node.js y npm instalados.
- **Claude no ve las tools:** reinicia la app.
- **Error de permisos:** revisa las rutas en la configuración.

## Notas

- El registro de MCP está en [modelcontextprotocol.io](https://modelcontextprotocol.io/).
- Los servidores se ejecutan como procesos locales.
- Sin coste adicional (solo el uso de Claude).
