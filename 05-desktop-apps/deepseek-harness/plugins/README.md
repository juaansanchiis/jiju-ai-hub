# Plugins de DeepSeek Harness

Extensiones o scripts para ampliar las capacidades de modelos o entornos basados en DeepSeek.

## Remotion Video Plugin (`chenjie1129/remotion-video-plugin`)

- **Qué hace:** Permite a agentes autónomos (como los de DeepSeek Harness) crear, previsualizar y renderizar vídeos basados en código React (Remotion) de forma verificada.
- **Flujo:** El agente escribe animaciones fotograma a fotograma usando `useCurrentFrame()`, `interpolate()` y componentes de vídeo, revisa las imágenes estáticas resultantes (stills) y exporta un vídeo limpio en H.264 sin dependencias de servicios cloud de pago.
- **Enlace:** [GitHub](https://github.com/chenjie1129/remotion-video-plugin)

## Otros ejemplos de plugins

- Wrapper de tool calling para funciones locales.
- Integración con IDEs (VS Code, JetBrains).
- Scripts de post-procesado de respuestas (formateo, validación).

## Estructura sugerida

```
plugins/
├── remotion-video/
├── tool-calling/
├── ide-integration/
└── post-processing/
```

## Notas

- Documenta cada plugin con su propósito, dependencias y uso.
- Mantén los plugins desacoplados del modelo base.
