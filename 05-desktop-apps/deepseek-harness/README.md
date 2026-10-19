# DeepSeek Harness

Configuración para exprimir al máximo los modelos de DeepSeek (tanto vía API como en local si usas versiones destiladas).

## Modelos disponibles

- **DeepSeek-V3:** Modelo general potente y económico.
- **DeepSeek-R1:** Modelo de razonamiento (chain-of-thought).
- **Versiones destiladas:** Para ejecución local con Ollama (ej. `deepseek-r1:8b`).

## Uso vía API

```bash
curl https://api.deepseek.com/chat/completions \
  -H "Authorization: Bearer $DEEPSEEK_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"deepseek-chat","messages":[{"role":"user","content":"Hola"}]}'
```

## Uso local (destilado)

```bash
ollama pull deepseek-r1:8b
ollama run deepseek-r1:8b
```

## Secciones

- [Plugins](plugins/README.md)
- [Conectores](connectors/README.md)
