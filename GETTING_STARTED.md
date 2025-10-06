# Guía de Inicio Rápido - MCP

## 🚀 Comenzando con MCP

Esta guía te ayudará a dar tus primeros pasos con Model Context Protocol.

## Prerrequisitos

- Node.js 18 o superior
- npm o yarn
- Git
- Editor de código (VS Code recomendado)

## Instalación Básica

### 1. Instalar la CLI de MCP

```bash
npm install -g @modelcontextprotocol/cli
```

### 2. Crear tu primer servidor MCP

```bash
mkdir mi-primer-servidor-mcp
cd mi-primer-servidor-mcp
npm init -y
npm install @modelcontextprotocol/sdk
```

### 3. Código básico de un servidor

```typescript
import { Server } from "@modelcontextprotocol/sdk/server/index.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";

// Crear servidor
const server = new Server(
  {
    name: "mi-servidor-mcp",
    version: "1.0.0",
  },
  {
    capabilities: {
      tools: {},
    },
  }
);

// Definir una herramienta
server.setRequestHandler(ListToolsRequestSchema, async () => {
  return {
    tools: [
      {
        name: "saludar",
        description: "Saluda a alguien",
        inputSchema: {
          type: "object",
          properties: {
            nombre: {
              type: "string",
              description: "Nombre de la persona",
            },
          },
          required: ["nombre"],
        },
      },
    ],
  };
});

// Iniciar servidor
const transport = new StdioServerTransport();
await server.connect(transport);
```

## Conectar con Claude Desktop

### 1. Ubicar el archivo de configuración

**Windows:**
```
%APPDATA%\Claude\claude_desktop_config.json
```

**macOS:**
```
~/Library/Application Support/Claude/claude_desktop_config.json
```

**Linux:**
```
~/.config/Claude/claude_desktop_config.json
```

### 2. Agregar tu servidor

```json
{
  "mcpServers": {
    "mi-servidor": {
      "command": "node",
      "args": ["/ruta/a/tu/servidor/index.js"]
    }
  }
}
```

### 3. Reiniciar Claude Desktop

Cierra y vuelve a abrir Claude Desktop para cargar el servidor.

## Servidores MCP Populares

### Filesystem Server
```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/ruta/permitida"]
    }
  }
}
```

### Git Server
```json
{
  "mcpServers": {
    "git": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-git"]
    }
  }
}
```

### GitHub Server
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "tu_token_aqui"
      }
    }
  }
}
```

## Primeros Pasos

### 1. Probar el servidor de archivos

Una vez configurado, puedes pedirle a Claude:
- "Lista los archivos en mi carpeta de proyectos"
- "Lee el contenido de README.md"
- "Crea un nuevo archivo llamado test.txt"

### 2. Probar Git y GitHub

- "Muéstrame el estado del repositorio"
- "Haz commit de los cambios"
- "Crea un Pull Request"

### 3. Crear tu propia herramienta

```typescript
server.setRequestHandler(CallToolRequestSchema, async (request) => {
  if (request.params.name === "saludar") {
    const nombre = request.params.arguments.nombre;
    return {
      content: [
        {
          type: "text",
          text: `¡Hola, ${nombre}! Bienvenido a MCP.`,
        },
      ],
    };
  }
  throw new Error("Herramienta no encontrada");
});
```

## Recursos Adicionales

- 📖 [Documentación completa](https://modelcontextprotocol.io/docs)
- 💬 [Discord de MCP](https://discord.gg/mcp)
- 🐙 [GitHub de MCP](https://github.com/modelcontextprotocol)
- 📺 [Tutoriales en video](https://youtube.com/@anthropic-ai)

## Solución de Problemas

### El servidor no aparece en Claude
1. Verifica que el path sea correcto
2. Asegúrate de tener Node.js instalado
3. Revisa los logs en la consola de desarrollo de Claude

### Error de permisos
- En Windows: Ejecuta como administrador
- En macOS/Linux: Verifica permisos con `chmod +x`

### El servidor no responde
- Verifica que el código no tenga errores de sintaxis
- Revisa que todas las dependencias estén instaladas
- Consulta los logs del servidor

## Próximos Pasos

1. ✅ Instalar y configurar MCP
2. ✅ Probar servidores existentes
3. 📝 Crear tu primer servidor custom
4. 🔧 Integrar con tus proyectos
5. 🚀 Compartir con la comunidad

---

¿Necesitas ayuda? Abre un issue en el repositorio o consulta la documentación oficial.
