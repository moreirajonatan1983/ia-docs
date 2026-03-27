# MCP Tools

> **Source:** [kiro.dev/docs/mcp/usage/](https://kiro.dev/docs/mcp/usage/)

---

Una vez configurados los MCP servers, podés usar sus tools directamente desde el chat.

---

## Interacting with MCP Tools

### Direct Questions

La forma más simple — hacé preguntas relacionadas al dominio del server:

```
Tell me about Amazon Bedrock
How do I configure S3 bucket policies?
```

Kiro selecciona automáticamente el MCP tool apropiado basado en tu pregunta.

### Specific Tool Requests

Describí lo que querés hacer:

```
Search AWS documentation for information about ECS task definitions
Get recommendations for AWS CloudFormation best practices
```

### Explicit Context

Para mayor control, especificá el server y el tool directamente:

```
#[aws-docs] search_documentation Tell me about AWS Lambda
```

Formato: `#[server-name] tool_name prompt`

---

## MCP Tools Panel

Accedé al panel de MCP Tools para gestionar los tools disponibles:

### Managing Individual Tools

- Ver todos los tools disponibles por server
- Habilitar o deshabilitar tools individuales
- Ver parámetros y descripción de cada tool

### Server-Level Actions

- Reiniciar un server MCP
- Ver logs del server
- Editar la configuración del server

---

## Tool Approval Process

Cuando Kiro quiere usar un MCP tool, solicita aprobación primero:

1. Aparece un prompt describiendo el tool y su propósito
2. Revisás los detalles del tool y los parámetros
3. Click **Approve** para permitir, o **Deny** para bloquear

### Auto-Approving Trusted Tools

Para tools de confianza de uso frecuente, configurá `autoApprove` en `mcp.json`:

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

## Examples by Server Type

### AWS Documentation Server

```
# Buscar documentación
Search AWS documentation for S3 bucket versioning

# Leer documentación específica
Read the AWS Lambda function URLs documentation

# Obtener recomendaciones
Find related content to AWS ECS task definitions
```

### GitHub MCP Server

```
# Info de repositorio
Show me information about the tensorflow/tensorflow repository

# Búsqueda de código
Find examples of React hooks in facebook/react

# Gestión de issues
Create an issue in my repository about the login bug
```

---

## Advanced Usage Techniques

### Chaining MCP Tools

Combiná múltiples tools en una sola conversación para tareas complejas. Por ejemplo, buscar documentación AWS y luego crear un issue en GitHub con el resultado.

### Combining with Local Context

Combina MCP tools con contexto local agregando archivos al contexto para que el agente pueda relacionar documentación externa con tu código actual.

### Using MCP Tools in Specs

Los MCP tools están disponibles durante la creación de Specs. Podés referenciarlos en el plan de implementación para que el agente los use durante la ejecución.

---

## MCP Prompts

Algunos MCP servers exponen **prompts predefinidos** — templates de prompts con parámetros:

### Accessing Prompts
Escribí `/` en el chat → los prompts MCP disponibles aparecerán junto a hooks y steering files.

### Prompts with Arguments
Los prompts pueden aceptar argumentos. Kiro te preguntará los valores necesarios antes de ejecutar el prompt.

---

## MCP Resource Templates

Algunos servers proveen **resource templates** — patrones de URI para acceder a recursos dinámicos:

### Accessing Resource Templates
Los templates aparecen en el panel de MCP Tools bajo cada server.

### Filling in Template Parameters
Completá los parámetros del template (ej. ID de repositorio, nombre de bucket) y Kiro generará el URI correcto para acceder al recurso.

---

## Best Practices

- Sé específico en tus requests para obtener los resultados más relevantes
- Empezá con preguntas directas antes de usar referencias explícitas de tools
- Auto-aprobá solo tools de confianza que uses frecuentemente
- Combiná MCP tools con contexto local para mejores resultados
- Revisá los parámetros del tool antes de aprobar para asegurarte que son correctos