# Indicaciones

> **Fuente:** [kiro.dev/docs/cli/chat/manage-prompts/](https://kiro.dev/docs/cli/chat/manage-prompts/)

---

Los avisos permiten crear, organizar y reutilizar instrucciones personalizadas para interacciones eficientes con el CLI.

---

## Tipos de mensajes

| Tipo | Descripción |
|---|---|
| **Mensajes locales** | Avisos específicos del proyecto, almacenados en el espacio de trabajo |
| **Mensajes globales** | Avisos disponibles en todos los proyectos |
| **Mensajes de MCP** | Avisos provistos por servidores MCP con funcionalidad extendida |

---

## Comandos

Todo el manejo de avisos se accede vía `/prompts`:

### Lista de mensajes
```
/lista de mensajes
```
Muestra todos los mensajes disponibles en diseño de 3 columnas: nombre, descripción y origen.

### Crear mensajes
```
/prompts create --name <nombre> [--content <contenido>]
```
- Si `--content` está provisto: crea el aviso con ese contenido
- Si no hay contenido: abre el editor por defecto
- Se guarda en `.kiro/prompts/` del espacio de trabajo actual
- Nombre máximo: 50 caracteres

### Editar mensajes
```
/solicita editar <nombre>
```
Abre el mensaje en el editor por defecto. Soporta solicita locales, globales y MCP.

### Ver detalles del mensaje
```
/solicita detalles <nombre>
```
Muestra: metadatos, argumentos, contenido completo, parámetros requeridos y origen.

---

## Uso de indicaciones

Invocará avisos en el chat con el prefijo `@`:

```bash
@prompt-name
@code-review          # Usa tu prompt local code-review
@src/auth.rs          # Incluye el contenido del archivo src/auth.rs
@crates/agent/        # Muestra la estructura del directorio
```

### Referencias de archivos y directorios (v1.26.0+)

También podés usar `@` para referenciar archivos y directorios:

```bash
> Review @src/auth.rs for security issues
> What's the structure of @crates/agent/?
> Check @"my file.txt" for errors
> Compare @./v1/api.rs with @./v2/api.rs
```

**Características:**
- Completar tabulación después de `@`
- Referencias resaltadas en violeta
- Archivos como bloques de código, directorios como árbol
- Límite: 250 KB por archivo, 3 niveles de profundidad, 10 elementos por nivel

**Reglas de prioridad:**
1. **Indica a conocidos** (local, global, MCP)
2. **Archivos** — ruta de archivo
3. **Directorios** — si no es archivo

---

## Ubicaciones de almacenamiento

| Alcance | Ubicación | Prioridad |
|---|---|---|
| **Local (espacio de trabajo)** | `proyecto/.kiro/prompts/` | ⬆️Más alta |
| **Global (todo el usuario)** | `~/.kiro/prompts/` | Medios |
| **MCP** | Información sobre el servidor MCP | ⬇️Más baja |

---

## Integración MCP

Los avisos de MCP son provistos por servidores MCP configurados. Soportan argumentos dinámicos:

```bash
> /prompts list        # Los prompts MCP aparecen con su origen
> /prompts details aws-docs  # Ver parámetros requeridos
```