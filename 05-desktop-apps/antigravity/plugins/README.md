# Plugins de Antigravity

Extensiones o scripts personalizados que utilices en tus flujos de desarrollo.

## Ejemplos de plugins

- Linters personalizados.
- Generadores de código.
- Integraciones con herramientas externas.
- Formateadores de código.
- Analizadores de dependencias.

## Estructura sugerida

```
plugins/
├── linters/
├── generators/
├── integrations/
├── formatters/
└── analyzers/
```

## Buenas prácticas

- Documenta dependencias y uso de cada plugin.
- Mantén los plugins modulares y testeables.
- Versiona los plugins en este repositorio.
- Prueba cada plugin de forma aislada.

## Solución de problemas

- **Plugin no carga:** verifica dependencias y versiones.
- **Error de ejecución:** revisa los logs.
- **Incompatibilidad:** verifica la versión del entorno.

## Notas

- Los plugins amplían las capacidades del entorno.
- Mantén la compatibilidad con el core.
