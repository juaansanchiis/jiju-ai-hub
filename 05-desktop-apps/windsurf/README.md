# Windsurf (Codeium)

IDE con IA integrada (de Codeium) que compite directamente con Cursor. Tiene un agente llamado "Cascade" que puede hacer cambios multi-archivo y razonar sobre el codebase completo.

- **Tipo:** IDE con IA integrada
- **Enlace:** [codeium.com/windsurf](https://codeium.com/windsurf)
- **Licencia:** Propietaria (freemium)

## Instalación

1. Descarga desde [codeium.com/windsurf](https://codeium.com/windsurf).
2. Instala y abre (compatible con Windows, macOS, Linux).
3. Inicia sesión con tu cuenta de Codeium.

## Características principales

- **Cascade (agente):** Agente que razona sobre el codebase y hace cambios multi-archivo.
- **Autocomplete (supercomplete):** Predicción de código multi-línea con contexto del proyecto.
- **Chat:** Chat con contexto del codebase.
- **Inline edit:** Edición inline con instrucciones.
- **Flows:** Flujos de trabajo automatizados (ej. "arregla todos los errores de lint").

## Modelos disponibles

| Modelo | Uso |
| --- | --- |
| GPT-4o | Chat, Cascade |
| Claude 3.5 Sonnet | Chat, Cascade |
| Codeium (propio) | Autocomplete (rápido) |
| Llama 3.1 | Chat (local via Ollama) |

## Planes

| Plan | Precio | Incluye |
| --- | --- | --- |
| Free | Gratis | Autocomplete ilimitado, 25 Cascade prompts/mes |
| Pro | $15/mes | Autocomplete ilimitado, 500 Cascade prompts/mes |
| Teams | $30/mes/usuario | Pro + admin, SSO |

## Casos de uso

- Desarrollo con agente (Cascade) para cambios complejos.
- Refactorización multi-archivo.
- Exploración de codebases (Chat con contexto).
- Generación de tests y documentación.
- Debugging asistido.

## Atajos de teclado

| Atajo | Acción |
| --- | --- |
| `Tab` | Aceptar autocomplete |
| `Cmd+K` | Edición inline |
| `Cmd+L` | Abrir chat |
| `Cmd+I` | Abrir Cascade |

## Cascade (agente)

Cascade es el agente principal de Windsurf. Puede:
- Leer y modificar múltiples archivos.
- Ejecutar comandos en la terminal.
- Buscar en el codebase.
- Razonar sobre la arquitectura del proyecto.
- Hacer cambios incrementales con revisión.

## Buenas prácticas

1. Usa Cascade para cambios complejos multi-archivo.
2. Usa autocomplete para escritura rápida.
3. Revisa siempre los diffs de Cascade.
4. Configura reglas de proyecto (.windsurfrules) para guiar al agente.
5. Usa modelos potentes para Cascade, modelos rápidos para autocomplete.

## .windsurfrules (reglas de proyecto)

```markdown
# .windsurfrules
- Usa TypeScript estricto.
- Sigue el patrón de arquitectura hexagonal.
- Escribe tests con Vitest.
- Usa 4 espacios para indentación.
```

## Comparación Cursor vs Windsurf

| Aspecto | Cursor | Windsurf |
| --- | --- | --- |
| Precio Pro | $20/mes | $15/mes |
| Agente | Composer | Cascade |
| Autocomplete | Tab (multi-archivo) | Supercomplete |
| Modelos | GPT-4o, Claude | GPT-4o, Claude, Codeium |
| Extensiones VS Code | Sí | Sí |
| Reglas de proyecto | .cursorrules | .windsurfrules |

## Troubleshooting

- **Cascade no responde:** Verifica tu conexión y límite de prompts.
- **Autocomplete lento:** Reduce el tamaño del proyecto indexado.
- **Chat sin contexto:** Usa @file o @folder para dar contexto.
- **Extensiones no funcionan:** Algunas extensiones de VS Code no son compatibles.
- **Límite de prompts:** Actualiza a Pro o espera al reset mensual.
