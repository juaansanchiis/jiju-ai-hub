# Plugins de DeepSeek Harness

Extensiones o scripts para ampliar las capacidades de modelos o entornos basados en DeepSeek.

## Ejemplos de plugins

- Wrapper de tool calling para funciones locales.
- Integración con IDEs (VS Code, JetBrains).
- Scripts de post-procesado de respuestas (formateo, validación).

## Estructura sugerida

```
plugins/
├── tool-calling/
├── ide-integration/
└── post-processing/
```

## Notas

- Documenta cada plugin con su propósito, dependencias y uso.
- Mantén los plugins desacoplados del modelo base.
