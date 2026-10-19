# Cursor

IDE (editor de código) que está destronando a VS Code. Tiene agentes integrados y predicción de código multi-archivo que parece magia. Basado en VS Code, por lo que es compatible con extensiones.

- **Tipo:** IDE con IA integrada
- **Enlace:** [cursor.com](https://www.cursor.com/)
- **Licencia:** Propietaria (freemium)

## Instalación

1. Descarga desde [cursor.com](https://www.cursor.com/).
2. Instala y abre (compatible con Windows, macOS, Linux).
3. Importa tu configuración de VS Code si quieres.

## Características principales

- **Tab (predicción multi-archivo):** Predice tu siguiente edición en múltiples archivos simultáneamente.
- **Composer (agente):** Agente que puede crear, editar y borrar archivos en todo el proyecto.
- **Chat (Cmd+L):** Chat con contexto del codebase (RAG sobre tu repo).
- **Inline edit (Cmd+K):** Edita código seleccionado con instrucciones en lenguaje natural.
- **@-mentions:** Referencia archivos, carpetas, docs, web, etc. en el chat.

## Modelos disponibles

| Modelo | Uso | Coste |
| --- | --- | --- |
| GPT-4o | Chat, Composer | Incluido en Pro |
| Claude 3.5 Sonnet | Chat, Composer | Incluido en Pro |
| Cursor Small | Tab (predicción) | Gratis |
| o1-mini | Razonamiento | Incluido en Pro |

## Planes

| Plan | Precio | Incluye |
| --- | --- | --- |
| Hobby | Gratis | 2000 completions, 50 slow premium requests |
| Pro | $20/mes | Unlimited completions, 500 fast premium requests |
| Business | $40/mes/usuario | Pro + admin, SSO, privacidad |

## Casos de uso

- Desarrollo full-stack con agente (Composer).
- Refactorización multi-archivo.
- Exploración de codebases desconocidos (Chat con @codebase).
- Generación de tests y documentación.
- Debugging con contexto completo.

## Atajos de teclado

| Atajo | Acción |
| --- | --- |
| `Tab` | Aceptar predicción |
| `Cmd+K` | Edición inline |
| `Cmd+L` | Abrir chat |
| `Cmd+I` | Abrir Composer |
| `Cmd+Shift+L` | Añadir selección al chat |

## Buenas prácticas

1. Usa @codebase para dar contexto del proyecto al chat.
2. Usa Composer para cambios multi-archivo.
3. Revisa siempre los diffs antes de aceptar.
4. Usa modelos potentes (Claude/GPT-4o) para Composer, modelos rápidos para Tab.
5. Configura reglas de proyecto (.cursorrules) para guiar al agente.

## .cursorrules (reglas de proyecto)

```markdown
# .cursorrules
- Usa TypeScript estricto.
- Sigue el patrón de arquitectura hexagonal.
- Escribe tests con Vitest.
- Usa 4 espacios para indentación.
- Comenta funciones públicas con JSDoc.
```

## Troubleshooting

- **Tab no predice:** Verifica que el modelo de Tab está activo.
- **Composer lento:** Usa un modelo más rápido o reduce el contexto.
- **Chat sin contexto:** Usa @codebase o @file para dar contexto.
- **Extensiones no funcionan:** Algunas extensiones de VS Code no son compatibles.
- **Límite de requests:** Actualiza a Pro o espera al reset mensual.
