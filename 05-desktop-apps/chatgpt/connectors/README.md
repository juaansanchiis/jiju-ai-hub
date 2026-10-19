# Conectores de ChatGPT

Cómo integrar ChatGPT con herramientas externas, APIs o bases de datos locales mediante conectores web o webhooks.

## Integración con herramientas externas

- Usa **Actions** en Custom GPTs para llamar a APIs REST.
- Conecta a bases de datos locales mediante servidores MCP o webhooks intermedios.
- Usa Zapier/Make como puente para servicios sin API directa.
- Usa túneles (ngrok, cloudflared) para exponer APIs locales.

## Ejemplo de Action (OpenAPI)

```yaml
openapi: 3.0.0
info:
  title: Mi API local
  version: 1.0.0
servers:
  - url: http://localhost:8080
paths:
  /query:
    post:
      operationId: queryData
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                text:
                  type: string
      responses:
        "200":
          description: OK
```

## Conectores populares

- **Google Drive / Docs:** Acceso a documentos.
- **GitHub:** Repositorios y issues.
- **Slack:** Mensajes y canales.
- **Notion:** Bases de datos y páginas.
- **Zapier:** Puente a miles de apps.

## Buenas prácticas

- Las Actions requieren HTTPS en producción; usa túneles para desarrollo local.
- Limita los permisos del conector al mínimo necesario.
- Valida inputs en tu API antes de procesar.
- Usa autenticación (API key, OAuth) en tus endpoints.

## Solución de problemas

- **Action no se ejecuta:** verifica el schema OpenAPI y la URL.
- **Error de CORS:** configura headers CORS en tu API.
- **Timeout:** optimiza el endpoint o aumenta el timeout.

## Notas

- Las Actions se definen en Custom GPTs.
- El conector debe ser accesible desde los servidores de OpenAI.
