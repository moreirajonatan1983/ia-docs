# Prompts

> **Source:** [kiro.dev/docs/cli/chat/manage-prompts/](https://kiro.dev/docs/cli/chat/manage-prompts/)

---

Los prompts permiten crear, organizar y reutilizar instrucciones personalizadas para interacciones eficientes con el CLI.

---

## Prompt Types

| Tipo | Descripción |
|---|---|
| **Local prompts** | Prompts específicos del proyecto, almacenados en el workspace |
| **Global prompts** | Prompts disponibles en todos los proyectos |
| **MCP prompts** | Prompts provistos por servidores MCP con funcionalidad extendida |

---

## Commands

Todo el manejo de prompts se accede vía `/prompts`:

### List Prompts
```
/prompts list
```
Muestra todos los prompts disponibles en layout de 3 columnas: nombre, descripción y origen.

### Create Prompts
```
/prompts create --name <nombre> [--content <contenido>]
```
- Si `--content` está provisto: crea el prompt con ese contenido
- Si no hay contenido: abre el editor por defecto
- Se guarda en `.kiro/prompts/` del workspace actual
- Nombre máximo: 50 caracteres

### Edit Prompts
```
/prompts edit <nombre>
```
Abre el prompt en el editor por defecto. Soporta prompts locales, globales y MCP.

### View Prompt Details
```
/prompts details <nombre>
```
Muestra: metadatos, argumentos, contenido completo, parámetros requeridos y origen.

---

## Using Prompts

Invocá prompts en el chat con el prefijo `@`:

```bash
@prompt-name
@code-review          # Usa tu prompt local code-review
@src/auth.rs          # Incluye el contenido del archivo src/auth.rs
@crates/agent/        # Muestra la estructura del directorio
```

### File and Directory References (v1.26.0+)

También podés usar `@` para referenciar archivos y directorios:

```bash
> Review @src/auth.rs for security issues
> What's the structure of @crates/agent/?
> Check @"my file.txt" for errors
> Compare @./v1/api.rs with @./v2/api.rs
```

**Features:**
- Tab completion después de `@`
- Referencias resaltadas en violeta
- Archivos como code blocks, directorios como árbol
- Límite: 250KB por archivo, 3 niveles de profundidad, 10 items por nivel

**Priority Rules:**
1. **Prompts conocidos** (local, global, MCP)
2. **Archivos** — path de archivo
3. **Directorios** — si no es archivo

---

## Storage Locations

| Scope | Ubicación | Prioridad |
|---|---|---|
| **Local (workspace)** | `project/.kiro/prompts/` | ⬆️ Más alta |
| **Global (user-wide)** | `~/.kiro/prompts/` | Media |
| **MCP** | Provisto por el servidor MCP | ⬇️ Más baja |

---

## MCP Integration

Los prompts de MCP son provistos por servidores MCP configurados. Soportan argumentos dinámicos:

```bash
> /prompts list        # Los prompts MCP aparecen con su origen
> /prompts details aws-docs  # Ver parámetros requeridos
```