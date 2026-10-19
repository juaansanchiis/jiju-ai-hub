# Custom GPTs de ChatGPT

Prompts maestros, instrucciones de sistema (*system prompts*) y ejemplos de Actions para crear Custom GPTs avanzados y ultra específicos.

## System prompt maestro (plantilla)

```
Eres un asistente experto en [DOMINIO]. Tu objetivo es [OBJETIVO].
Reglas:
- Responde siempre en español.
- Si no sabes algo, dilo claramente.
- Usa herramientas (Actions) cuando necesites datos externos.
- Formatea las respuestas con Markdown.
- No inventes datos; cita fuentes cuando sea posible.
```

## Ejemplos de Actions

- Consultar una base de datos interna vía API.
- Buscar en documentación propia.
- Ejecutar cálculos o transformaciones de datos.
- Enviar emails o mensajes.

## Buenas prácticas

- Define claramente el alcance y las limitaciones del GPT.
- Añade ejemplos de conversación (few-shot) en las instrucciones.
- Versiona los prompts en este repositorio.
- Prueba con casos límite antes de publicar.
- Usa "Knowledge" para subir documentos de referencia.

## Ideas de Custom GPTs

- **Code Reviewer:** Revisa PRs con checklist de seguridad y estilo.
- **Doc Generator:** Genera documentación a partir de código.
- **Data Analyst:** Consulta bases de datos y genera gráficos.
- **Email Assistant:** Redacta y envía emails con contexto.

## Solución de problemas

- **GPT no sigue instrucciones:** simplifica el prompt, añade ejemplos.
- **Actions fallan:** verifica el schema y la autenticación.
- **Knowledge no se usa:** asegúrate de que los archivos estén bien formateados.

## Tabla resumen

| GPT | Enlace | Notas |
| --- | --- | --- |
| Por añadir | — | — |
