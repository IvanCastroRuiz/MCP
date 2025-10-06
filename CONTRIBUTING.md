# Contribuir a MCP

¡Gracias por tu interés en contribuir! 🎉

## 🤝 Cómo Contribuir

### Reportar Bugs

Si encuentras un bug:

1. Verifica que no exista un issue similar
2. Crea un nuevo issue con:
   - Descripción clara del problema
   - Pasos para reproducir
   - Comportamiento esperado vs actual
   - Screenshots si aplica
   - Información del entorno (OS, Node version, etc.)

### Sugerir Mejoras

Para nuevas features o mejoras:

1. Abre un issue describiendo:
   - El problema que resuelve
   - La solución propuesta
   - Alternativas consideradas
   - Impacto en el proyecto

### Pull Requests

#### Proceso

1. **Fork** el repositorio
2. **Crea una branch** desde `main`:
   ```bash
   git checkout -b feature/mi-nueva-feature
   ```
3. **Haz tus cambios** siguiendo las guías de estilo
4. **Commit** con mensajes descriptivos:
   ```bash
   git commit -m "feat: agrega nueva funcionalidad X"
   ```
5. **Push** a tu fork:
   ```bash
   git push origin feature/mi-nueva-feature
   ```
6. **Abre un PR** con descripción detallada

#### Guía de Commits

Seguimos [Conventional Commits](https://www.conventionalcommits.org/):

- `feat:` Nueva funcionalidad
- `fix:` Corrección de bug
- `docs:` Cambios en documentación
- `style:` Formato, sin cambios de código
- `refactor:` Refactorización de código
- `test:` Agregar o corregir tests
- `chore:` Tareas de mantenimiento

Ejemplos:
```bash
feat: agrega servidor MCP para PostgreSQL
fix: corrige error en manejo de archivos grandes
docs: actualiza guía de instalación
refactor: mejora estructura del código del servidor Git
```

## 📋 Checklist para PRs

Antes de abrir un PR, verifica:

- [ ] El código sigue el estilo del proyecto
- [ ] Has actualizado la documentación si es necesario
- [ ] Has agregado tests si aplica
- [ ] Todos los tests pasan
- [ ] El commit sigue Conventional Commits
- [ ] Has probado los cambios localmente
- [ ] La branch está actualizada con `main`

## 🎨 Guía de Estilo

### TypeScript/JavaScript

```typescript
// ✅ Bien
function procesarDatos(datos: string[]): Promise<Result> {
  return datos.map(item => item.trim());
}

// ❌ Evitar
function procesamosDatos(d) {
  return d.map(x=>x.trim())
}
```

### Documentación

- Usa Markdown para documentos
- Incluye ejemplos de código
- Agrega screenshots cuando sea útil
- Mantén los enlaces actualizados

### Nombres de Archivos

- `kebab-case` para archivos: `mi-servidor-mcp.ts`
- `PascalCase` para clases: `ServerManager.ts`
- `camelCase` para funciones: `procesarDatos()`

## 🧪 Testing

### Ejecutar Tests

```bash
npm test
```

### Escribir Tests

```typescript
describe("MCP Server", () => {
  it("debe inicializar correctamente", async () => {
    const server = new MCPServer();
    await server.start();
    expect(server.isRunning()).toBe(true);
  });
});
```

## 📖 Documentación

### Agregar Documentación

1. Actualiza el README si cambias funcionalidad principal
2. Agrega comentarios JSDoc en el código:
   ```typescript
   /**
    * Procesa los datos entrantes
    * @param datos - Array de strings a procesar
    * @returns Promise con resultado procesado
    */
   ```
3. Crea guías en la carpeta `docs/` si es necesario

## 🌟 Áreas de Contribución

### Buenas primeras contribuciones

- Corregir typos en documentación
- Agregar ejemplos de uso
- Mejorar mensajes de error
- Agregar tests

### Contribuciones intermedias

- Implementar nuevas features
- Optimizar performance
- Mejorar manejo de errores
- Agregar validaciones

### Contribuciones avanzadas

- Diseñar nuevos servidores MCP
- Mejorar arquitectura
- Implementar nuevos protocolos
- Contribuir a la especificación MCP

## 🐛 Debugging

### Logs

```typescript
import { logger } from "./logger";

logger.debug("Mensaje de debug");
logger.info("Información general");
logger.warn("Advertencia");
logger.error("Error", error);
```

### Herramientas

- VS Code con debugger configurado
- Chrome DevTools para código cliente
- MCP Inspector para probar servidores

## 📝 Licencia

Al contribuir, aceptas que tu código será licenciado bajo la misma licencia del proyecto.

## 💬 Comunicación

- **Issues**: Para bugs y features
- **Discussions**: Para preguntas y discusiones
- **Discord**: Para chat en tiempo real

## 🙏 Agradecimientos

Gracias a todos los contribuidores que hacen este proyecto posible!

---

¿Preguntas? No dudes en abrir un issue o contactarnos.
