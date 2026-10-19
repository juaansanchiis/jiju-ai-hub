# Antigravity

Documentación general de este entorno/proyecto, arquitectura y cómo arrancarlo.

## Arquitectura

- **Frontend:** (por definir)
- **Backend:** (por definir)
- **Agentes:** (por definir)
- **Base de datos:** (por definir)

## Cómo arrancarlo

```bash
# Clonar e instalar dependencias
git clone <repo>
cd antigravity
npm install   # o el gestor correspondiente

# Arrancar en desarrollo
npm run dev
```

## Variables de entorno

```bash
# .env
API_KEY=...
DATABASE_URL=...
MODEL_PROVIDER=openrouter
```

## Secciones

- [Skills](skills/README.md)
- [Plugins](plugins/README.md)

## Buenas prácticas

- Mantén la documentación actualizada.
- Usa control de versiones para skills y plugins.
- Prueba en entorno aislado antes de producción.

## Solución de problemas

- **No arranca:** verifica dependencias y variables de entorno.
- **Error de conexión:** revisa la configuración de red.
- **Tests fallan:** revisa los logs y la configuración.

## Notas

- Entorno propio para desarrollo con IA.
- Documentación interna del proyecto.
