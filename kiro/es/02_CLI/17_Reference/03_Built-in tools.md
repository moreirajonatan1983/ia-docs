# Herramientas integradas

> **Fuente:** [kiro.dev/docs/cli/reference/built-in-tools/](https://kiro.dev/docs/cli/reference/built-in-tools/)

---

## Descripción general

Las herramientas integradas son las capacidades nativas que Kiro CLI puede usar para interactuar con el sistema de archivos, ejecutar comandos, buscar en la web, y más.

---

## Archivo leído

Lee el contenido de archivos locales.

**Opciones de configuración:**
```json
{
  "Configuración de herramientas": {
    "leer": {
      "rutaspermitidas": ["src/**", "docs/**"],
      "rutas denegadas": [".env", "**/*.key"]
    }
  }
}
```

---

## globo

Busca usando archivos patrones glob.

**Opciones de configuración:**
```json
{
  "Configuración de herramientas": {
    "globo": {
      "rutas permitidas": ["./src/**"]
    }
  }
}
```

Ejemplo de uso: `Buscar todos los archivos TypeScript en el directorio src`

---

## grep

Busca texto en archivos usando expresiones regulares.

**Opciones de configuración:**
```json
{
  "Configuración de herramientas": {
    "grep": {
      "rutas permitidas": ["./src/**"],
      "resultados máximos": 100
    }
  }
}
```

---

## Escritura de archivo

Escribe o modifica archivos locales.

**Herramientas de diferenciación personalizadas:** Podés configurar herramientas externas como `delta`, `difftastic`, etc. Ver [Herramientas de diferenciación personalizadas →](../03_Chat/14_Custom diff tools.md).

**Opciones de configuración:**
```json
{
  "Configuración de herramientas": {
    "escribir": {
      "allowedPaths": ["src/**", "pruebas/**", "Cargo.toml"],
      "deniedPaths": [".env", "**/*.lock"]
    }
  }
}
```

---

## Ejecutar comandos de Shell

Ejecuta comandos shell en el sistema.

**Opciones de configuración:**
```json
{
  "Configuración de herramientas": {
    "cáscara": {
      "allowedCommands": ["estado de git", "prueba npm", "construcción de carga"],
      "deniedCommands": ["rm -rf .*", "sudo .*"],
      "autoAllowReadonly": verdadero
    }
  }
}
```

> `autoAllowReadonly: true` — preaprueba automáticamente comandos de solo lectura.

---

## Ejecutar comandos de AWS

Permite ejecutar comandos de AWS CLI directamente. Requiere que `aws-cli` esté instalado y configurado.

```
"Run aws s3 ls to list my buckets"
"Check the status of my CloudFormation stack"
```

---

## Búsqueda y recuperación web

### búsqueda_web
Busca información en la web.

### web_fetch
Obtiene contenido de URL específicas.

**Modos de búsqueda:**
| Modo | Descripción |
|---|---|
| `auto` | Kiro elige el mejor modo |
| `crudo` | HTML sin procesar |
| `texto` | Texto plano extraido |
| `rebaja` | Convertir a Markdown |

**Configuración:**
```json
{
  "Configuración de herramientas": {
    "web_search": { "habilitado": verdadero },
    "web_fetch": { "habilitado": verdadero }
  }
}
```

**Limitaciones:**
- No puede acceder a páginas que requieren autenticación
- Algunas páginas pueden bloquear el acceso programático
- Se pueden aplicar límites de tarifas

---

## Introspeccione las capacidades de Kiro CLI

Herramienta que permite a Kiro responder preguntas sobre sus propias capacidades, configuración y estado.

**Preguntas de ejemplo:**
- "¿Cuáles son los comandos disponibles?"
- "¿Cómo configurar un servidor MCP?"
- "¿Qué agente estoy usando actualmente?"

---

## Inteligencia de código

Integración con Language Server Protocol (LSP) para análisis de código avanzado:
- Información de desplazamiento
- Ir a la definición
- Encuentra referencias
- Diagnóstico de código

Inicializar con `/code init` en el chat.

---

## Delegar tareas (experimental)

Permite lanzar tareas asíncronas en segundo plano. Ver [Delegar →](../09_Experimental/06_Delegate.md).

---

## Enviar problema/solicitud de función

Herramienta para crear issues en GitHub directamente desde el chat. También disponible como `/issue`.

---

## Herramienta de conocimiento (experimental)

Acceso a la base de conocimiento para búsqueda semántica persistente. Ver [Gestión del Conocimiento →](../09_Experimental/01_Gestión del Conocimiento.md).

---

## Herramienta de pensamiento (experimental)

Muestra el proceso de razonamiento de la IA paso a paso. Ver [Herramienta de pensamiento →](../09_Experimental/04_Thinking tool.md).

---

## Herramienta de lista de tareas pendientes (experimental)

Gestión de listas de tareas persistentes. Ver [Listas TODO →](../09_Experimental/03_TODO listas.md).

---

## Permisos de herramientas

Por defecto, Kiro solicita commit para herramientas que pueden modificar el sistema:

| Herramienta | Permiso por defecto |
|---|---|
| `leer` | Auto aprobado |
| `globo` | Auto aprobado |
| `grep` | Auto aprobado |
| `escribir` | Requiere commit |
| `cáscara` | Requiere commit |
| `aws` | Requiere commit |
| `búsqueda_web` | Auto aprobado |
| `web_fetch` | Auto aprobado |

Gestioná permisos con `/tools trust`, `/tools untrust`, `/tools trust-all`.

---

## Uso de la configuración de herramientas en la configuración del agente

```json
{
  "toolsSettings": {
    "write": { "allowedPaths": ["src/**"] },
    "shell": {
      "allowedCommands": ["git status", "npm test"],
      "autoAllowReadonly": true
    },
    "@custom-mcp/my_tool": {
      "custom_param": "value"
    }
  }
}
```