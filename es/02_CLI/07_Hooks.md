# Hooks — Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/hooks/](https://kiro.dev/docs/cli/hooks/)

---

Los hooks le permiten ejecutar comandos personalizados en puntos específicos durante el ciclo de vida del agente y la ejecución de la herramienta. Le permiten validar acciones automáticamente, inyectar contexto o ejecutar tareas de posprocesamiento.

---

## Definición de hooks

Los enlaces se definen en el archivo de configuración del agente. Consulte la [Referencia de configuración del agente](https://kiro.dev/docs/cli/custom-agents/configuration-reference#hooks-field) para obtener la sintaxis completa.

---

## Evento de gancho

Los hooks reciben un evento de gancho en **formato JSON a través de STDIN**:

```json
{ "hook_event_name": "agentSpawn", "cwd": "/current/working/directory" }
```

Para los hooks relacionados con herramientas, se incluyen campos adicionales:
- `tool_name` — Nombre de la herramienta que se está ejecutando
- `tool_input` — Parámetros específicos de la herramienta
- `tool_response` — Resultados de ejecución de la herramienta *(solo PostToolUse)*

---

## Salida de gancho

| Código de salida | Comportamiento |
|---|---|
| `0` | Hook tuvo éxito. STDOUT se captura pero no se muestra al usuario. |
| `2` | *(Solo PreToolUse)* Bloquear la ejecución de la herramienta. STDERR se devuelve al LLM. |
| Otro | El gancho falló. STDERR se muestra como una advertencia para el usuario. |

---

## Coincidencia de herramientas

Utilice el campo `matcher` para especificar a qué herramientas se aplica el gancho:

| Emparejador | Partidos |
|---|---|
| `"fs_write"` o `"escribir"` | Herramienta de escritura |
| `"fs_read"` o `"read"` | Herramienta de lectura |
| `"execute_bash"` o `"shell"` | Ejecución del comando Shell |
| `"use_aws"` o `"aws"` | Herramienta AWS CLI |
| `"@git"` | Todas las herramientas del servidor git MCP |
| `"@git/estado"` | Herramienta específica del servidor git MCP |
| `"*"` | Todas las herramientas (integradas y MCP) |
| `"@integrado"` | Sólo todas las herramientas integradas |
| *(sin igualador)* | Se aplica a todas las herramientas |

---

## Tipos de gancho

### AgenteSpawn

Se ejecuta cuando se activa el agente. No se proporciona contexto de herramienta.

```json
{ "hook_event_name": "agentSpawn", "cwd": "/actual/trabajo/directorio" }
```
- Salir `0`: STDOUT se agrega al contexto del agente
- Otro: muestra la advertencia STDERR al usuario

---

### Aviso de usuarioEnviar

Se ejecuta cuando el usuario envía un mensaje. La salida se agrega al contexto de la conversación.

```json
{ "hook_event_name": "userPromptSubmit", "cwd": "/current/working/directory", "prompt": "mensaje de entrada del usuario" }
```
- Salir `0`: STDOUT se agrega al contexto del agente
- Otro: muestra la advertencia STDERR al usuario

---

### Uso previo de la herramienta

Se ejecuta **antes** de la ejecución de la herramienta. Puede validar y bloquear el uso de herramientas.

```json
{
  "hook_event_name": "preToolUse",
  "cwd": "/actual/trabajo/directorio",
  "nombre_herramienta": "leer",
  "tool_input": { "operaciones": [{ "modo": "Línea", "ruta": "/docs/hooks.md" }] }
}
```
- Salir `0`: Permitir la ejecución de la herramienta
- Salir `2`: Bloquear la ejecución de la herramienta, devolver STDERR a LLM
- Otro: muestra la advertencia STDERR, permite la ejecución de la herramienta

---

### Uso de la herramienta posterior

Se ejecuta **después** de la ejecución de la herramienta con acceso a los resultados de la herramienta.

```json
{
  "hook_event_name": "postToolUse",
  "nombre_herramienta": "leer",
  "tool_input": {...},
  "tool_response": { "éxito": verdadero, "resultado": ["..."] }
}
```
- Salir `0`: Hook exitoso
- Otro: Mostrar advertencia STDERR (la herramienta ya se ejecutó)

---

### Detener

Corre cuando el asistente termina de responder (fin de cada turno). Útil para el posprocesamiento: compilación, prueba, formateo o limpieza.

```json
{ "hook_event_name": "stop", "cwd": "/current/working/directory" }
```

> Nota: Los hooks de parada no utilizan comparadores ya que no se relacionan con herramientas específicas.

---

### Ejemplo de herramienta MCP

Para las herramientas MCP, el nombre de la herramienta incluye el formato de espacio de nombres completo:

```json
{
  "hook_event_name": "preToolUse",
  "tool_name": "@postgres/query",
  "tool_input": { "sql": "SELECT * FROM orders LIMIT 10;" }
}
```

---

## Se acabó el tiempo

El tiempo de espera predeterminado es **30 segundos** (30 000 ms). Configure con el campo `timeout_ms` en la configuración de su agente.

---

## Almacenamiento en caché

Los resultados del enlace exitoso se almacenan en caché según `cache_ttl_segundos`:

| Valor | Comportamiento |
|---|---|
| `0` | Sin almacenamiento en caché (predeterminado) |
| `> 0` | Almacenar en caché los resultados exitosos durante segundos específicos |
| — | Los hooks `AgentSpawn` nunca se almacenan en caché |