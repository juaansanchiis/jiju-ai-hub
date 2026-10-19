# Skills de Antigravity

Prompts estructurados, flujos de razonamiento o habilidades modulares que le enseñes a tus agentes o entornos de trabajo.

## Estructura de una skill

```markdown
# Nombre de la skill

## Objetivo
Descripción breve.

## Instrucciones
Pasos detallados.

## Ejemplos
Casos de uso concretos.

## Restricciones
Lo que NO debe hacer.
```

## Ejemplos de skills

- **Code review:** Revisar PRs con checklist de seguridad y estilo.
- **Refactor:** Simplificar código manteniendo tests.
- **Documentación:** Generar docs a partir del código.
- **Testing:** Generar tests unitarios.
- **Debugging:** Analizar errores y proponer fixes.

## Buenas prácticas

- Versiona las skills en este repositorio.
- Mantén cada skill autocontenida y reutilizable.
- Incluye ejemplos y restricciones.
- Prueba las skills con casos reales.

## Solución de problemas

- **Skill no se activa:** verifica el formato y la ubicación.
- **Resultados inconsistentes:** mejora las instrucciones y añade ejemplos.
- **Skill demasiado larga:** divide en skills más pequeñas.

## Notas

- Las skills son prompts reutilizables.
- Pueden combinarse para flujos complejos.
