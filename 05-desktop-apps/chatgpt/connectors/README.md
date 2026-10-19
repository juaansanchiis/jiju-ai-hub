# Conectores de ChatGPT

Cómo integrar ChatGPT con herramientas externas, APIs o bases de datos locales mediante conectores web o webhooks.

## Integración con herramientas externas

- Usa **Actions** en Custom GPTs para llamar a APIs REST.
- Conecta a bases de datos locales mediante servidores MCP o webhooks intermedios.
- Usa Zapier/Make como puente para servicios sin API directa.

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

## Notas

- Las Actions requieren HTTPS en producción; usa túneles (ngrok) para desarrollo local.
- Limita los permisos del conector al mínimo necesario.
