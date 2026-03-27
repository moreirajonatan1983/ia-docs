# Herramientas MCP

> **Fuente:** [kiro.dev/docs/mcp/usage/](https://kiro.dev/docs/mcp/usage/)

---

Una vez configurados los servidores MCP, podrás usar sus herramientas directamente desde el chat.

---

## Interactuar con herramientas MCP

### Preguntas directas

La forma más simple — hacé preguntas relacionadas al dominio del servidor:

```
Tell me about Amazon Bedrock
How do I configure S3 bucket policies?
```

Kiro selecciona automáticamente la herramienta MCP apropiada basada en tu pregunta.

### Solicitudes de herramientas específicas

Describí lo que querés hacer:

```
Search AWS documentation for information about ECS task definitions
Get recommendations for AWS CloudFormation best practices
```

### Contexto explícito

Para mayor control, especifique el servidor y la herramienta directamente:

```
#[aws-docs] search_documentation Tell me about AWS Lambda
```

Formato: `#[nombre-servidor] mensaje nombre_herramienta`

---

## Panel de herramientas MCP

Accedé al panel de MCP Tools para gestionar las herramientas disponibles:

### Gestión de herramientas individuales

- Ver todas las herramientas disponibles por servidor.
- Habilitar o deshabilitar herramientas individuales
- Ver parámetros y descripción de cada herramienta.

### Acciones a nivel de servidor

- Reiniciar un servidor MCP
- Ver registros del servidor
- Editar la configuración del servidor

---

## Proceso de aprobación de herramientas

Cuando Kiro quiera usar una herramienta MCP, solicita aprobación primero:

1. Aparece un mensaje que describe la herramienta y su propósito.
2. Revisarás los detalles de la herramienta y los parámetros.
3. Haga clic en **Aprobar** para permitir, o **Denegar** para bloquear.

### Herramientas confiables de aprobación automática

Para herramientas de confianza de uso frecuente, configure `autoApprove` en `mcp.json`:

```json
{
  "mcpServers": {
    "aws-docs": {
      "autoApprove": [
        "mcp_aws_docs_search_documentation",
        "mcp_aws_docs_read_documentation"
      ]
    }
  }
}
```

---

## Ejemplos por tipo de servidor

### Servidor de documentación de AWS

```
#Buscar documentación
Busque en la documentación de AWS el control de versiones del depósito S3

# Leer documentación específica
Lea la documentación de las URL de la función AWS Lambda

#recomendaciones Obtener
Encuentre contenido relacionado con las definiciones de tareas de AWS ECS
```

### Servidor MCP de GitHub

```
# Información del repositorio
Muéstrame información sobre el repositorio tensorflow/tensorflow

# Búsqueda de código
Encuentre ejemplos de hooks de React en facebook/react

# Gestión de emisiones
Crear un problema en mi repositorio sobre el error de inicio de sesión
```

---

## Técnicas de uso avanzadas

### Encadenamiento de herramientas MCP

Combina múltiples herramientas en una sola conversación para tareas complejas. Por ejemplo, busque documentación AWS y luego cree un problema en GitHub con el resultado.

### Combinando con el contexto local

Combina herramientas MCP con contexto local agregando archivos al contexto para que el agente pueda relacionar documentación externa con tu código actual.

### Uso de herramientas MCP en especificaciones

Las herramientas MCP están disponibles durante la creación de Specs. Podés referenciarlos en el plan de implementación para que el agente los use durante la ejecución.

---

## Avisos de MCP

Algunos servidores MCP exponen **indicaciones predefinidas** — plantillas de indicaciones con parámetros:

### Acceso a indicaciones
Escribí `/` en el chat → los avisos MCP disponibles aparecerán junto a hooks y archivos de Steering.

### Indicaciones con argumentos
Los avisos pueden aceptar argumentos. Kiro te preguntará los valores necesarios antes de ejecutar el aviso.

---

## Plantillas de recursos de MCP

Algunos servidores proporcionan **plantillas de recursos** — patrones de URI para acceder a recursos dinámicos:

### Acceso a plantillas de recursos
Las plantillas aparecen en el panel de MCP Tools bajo cada servidor.

### Completar los parámetros de la plantilla
Completará los parámetros de la plantilla (ej. ID de repositorio, nombre de depósito) y Kiro generará el URI correcto para acceder al recurso.

---

## Mejores prácticas

- Sé específico en tus solicitudes para obtener los resultados más relevantes.
- Empezá con preguntas directas antes de usar referencias específicas de herramientas.
- Auto-aprobá solo herramientas de confianza que usas frecuentemente
- Combiná herramientas MCP con contexto local para mejores resultados
- Revisá los parámetros de la herramienta antes de aprobar para asegurarte que son correctos.