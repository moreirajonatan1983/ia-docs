# Terminal Integration

> **Source:** [kiro.dev/docs/chat/terminal/](https://kiro.dev/docs/chat/terminal/)

---

En lugar de memorizar sintaxis de comandos o cambiar entre ventanas, describí lo que querés hacer y Kiro traduce tus solicitudes en comandos ejecutables, mantiene contexto entre operaciones, y provee un sistema de aprobación seguro.

---

## Getting Started

Simplemente describí lo que querés hacer en lenguaje natural:

- "Install the project dependencies"
- "Check the git status"
- "Find all TypeScript files in the src folder"
- "Run the development server"

Kiro traduce tu solicitud al comando apropiado y pide aprobación antes de ejecutar.

---

## How It Works

Cuando Kiro sugiere un comando, tenés cuatro opciones:

| Opción | Acción |
|---|---|
| **Modify** | Editar el comando antes de ejecutar |
| **Reject** | Cancelar la ejecución |
| **Run** | Ejecutar una vez |
| **Run and Trust** | Ejecutar y confiar en comandos similares en el futuro |

Los comandos de larga ejecución (como dev servers) son gestionados automáticamente por Kiro en terminales dedicadas sin bloquear tu workflow.

---

## Command Approval & Security

### Trust Commands

Configurá qué comandos confiar automáticamente en:
**Settings → Kiro Agent: Trusted Commands**

Disponible a nivel usuario (global) y a nivel workspace.

#### Exact matching
```json
["npm install", "git status"]
```
- ✅ `npm install` → auto-approved
- ✅ `git status` → auto-approved
- ❌ `npm install --save` → requires approval (exact match only)

#### Partial wildcard matching
```json
["npm install *"]
```
- ✅ `npm install` → approved
- ✅ `npm install --save` → approved
- ✅ `npm install express` → approved
- ❌ `npm run build` → requires approval

#### Full wildcard matching
```json
["npm *", "git *"]
```
- ✅ Todos los comandos `npm` y `git` → auto-approved
- ❌ `docker build .` → requires approval

#### Universal trust
```json
["*"]
```
> ⚠️ **Extremadamente peligroso.** Solo usá esto si controlás completamente el ambiente.

### Command Denylist

La lista de denegación previene la auto-aprobación de comandos con patrones específicos, independientemente de los trust settings. Usa **substring matching**.

**Settings → Kiro Agent: Command Denylist**

```json
{
  "kiroAgent.commandDenylist": [
    "rm -rf",
    "sudo",
    "chmod 777",
    "eval",
    "curl | sh",
    "wget | sh",
    "> /dev/",
    "mkfs",
    "dd if="
  ]
}
```

> La denylist **se chequea antes** que los trust settings. Incluso con `["*"]` en trusted, los comandos denegados requieren aprobación manual.

---

## Using Terminal Context

Referenciá la salida reciente de tu terminal con `#terminal`:

```
#terminal analyze the error from the last npm run build
```

> ⚠️ `#terminal` siempre hace referencia a la terminal activa/visible. Si tenés múltiples terminales abiertas, asegurate que la correcta esté activa antes de usar `#terminal`.

**Capacidades:**
- Error Analysis — Entender por qué fallaron los comandos
- Output Interpretation — Explicar resultados complejos y logs
- Follow-up Actions — Sugerir próximos pasos basados en resultados reales
- Pattern Recognition — Identificar problemas recurrentes
- Environment Debugging — Resolver conflictos de sistema y dependencias