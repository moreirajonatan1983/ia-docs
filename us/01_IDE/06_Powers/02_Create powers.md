# Create Powers

> **Source:** [kiro.dev/docs/powers/create/](https://kiro.dev/docs/powers/create/)

---

Creá tus propios powers para extender las capacidades de Kiro con herramientas especializadas, y compartílos con la comunidad.

---

## What You Need

Todo power necesita un archivo `POWER.md`. Opcionalmente podés agregar:

- `mcp.json` — Configuración de MCP servers para integraciones de tools
- `steering/` — Archivos de guidance específicos por workflow

---

## Creating POWER.md

El archivo `POWER.md` tiene dos partes: **frontmatter** e **instrucciones para el agente**.

### Frontmatter: When to Activate

El frontmatter le dice a Kiro cuándo cargar tu power. Usá keywords que coincidan con cómo los developers hablan de tu herramienta.

```yaml
---
name: "supabase"
displayName: "Supabase with local CLI"
description: "Build fullstack applications with Supabase's Postgres database, authentication, storage, and real-time subscriptions"
keywords: ["database", "postgres", "auth", "storage", "realtime", "backend", "supabase", "rls"]
---
```

**Cómo funciona:** Cuando alguien dice "Let's set up the database", Kiro ve "database" en los keywords y activa el Supabase power. Los MCP tools y la documentación del power se cargan automáticamente en contexto.

### Onboarding Instructions

La sección de onboarding corre cuando alguien usa tu power por primera vez. Usala para validar dependencias, explicar pasos de setup o crear workspace hooks.

```markdown
# Onboarding

## Step 1: Validate tools work
Before using Supabase Local MCP, ensure the following are installed:
- **Docker Desktop**: Verify with: `docker --version`
  - **CRITICAL**: If Docker is not installed or not running, DO NOT proceed.
- **Supabase CLI**: Verify with: `supabase --version`

## Step 2: Add hooks
Add a hook to `.kiro/hooks/review-advisors.kiro.hook`
```

Kiro sigue estas instrucciones automáticamente: verifica que Docker esté corriendo, valida la CLI e instala el hook de revisión en el workspace.

### Steering Instructions

**Enfoque simple** (sin steering files separados): Incluí toda la guidance directamente en `POWER.md` después de la sección de onboarding.

**Enfoque avanzado** (múltiples steering files): Para tools con muchos workflows distintos, mapeá cada workflow a un steering file específico:

```markdown
# When to Load Steering Files
- Setting up a database → `database-setup-workflow.md`
- Writing or formatting SQL code → `supabase-code-format-sql.md`
- Creating or modifying RLS policies → `supabase-database-rls-policies.md`
- Creating PostgreSQL functions → `supabase-database-functions.md`
- Setting up Next.js auth with Supabase SSR → `supabase-nextjs-supabase-auth.md`
- Implementing realtime features → `supabase-use-realtime.md`
```

Esto previene sobrecargar el contexto con todos los patrones de golpe — Kiro carga solo el steering relevante al workflow actual.

---

## Adding MCP Servers

Si tu power usa MCP tools, creá un archivo `mcp.json`. Los nombres de servidores deben coincidir con los referenciados en `POWER.md`.

```json
{
  "mcpServers": {
    "supabase-local": {
      "command": "npx",
      "args": ["-y", "@supabase/mcp-server-supabase"],
      "env": {
        "SUPABASE_URL": "${SUPABASE_URL}",
        "SUPABASE_ANON_KEY": "${SUPABASE_ANON_KEY}"
      }
    }
  }
}
```

> ⚠️ Usá variables de entorno para API keys y secrets. Durante la instalación, Kiro automáticamente namespaces los nombres de server para evitar conflictos (ej. `supabase-local` → `power-supabase-supabase-local`).

---

## Directory Structure

```
power-supabase/
├── POWER.md          # Metadata, onboarding, steering mappings
├── mcp.json          # MCP server configuration
└── steering/         # Workflow-specific guidance
    ├── database-setup-workflow.md
    ├── supabase-code-format-sql.md
    ├── supabase-database-rls-policies.md
    └── supabase-edge-functions.md
```

---

## Examples

| Tipo | Estructura |
|---|---|
| **Simple** (sin steering files) | `POWER.md` + `mcp.json` (opcional) |
| **Single-tool con steering** | `POWER.md` + `mcp.json` + `steering/schema-patterns.md` |
| **Multi-tool** | `POWER.md` + `mcp.json` + múltiples archivos en `steering/` |
| **Documentation-only** | `POWER.md` + `steering/` (sin MCP servers) |

---

## Testing Locally

1. Creá el directorio del power con los archivos necesarios
2. Abrí **Kiro → Powers panel → Add power from Local Path**
3. Seleccioná tu directorio del power
4. Testeá la activación usando keywords de tu power en una conversación

---

## Sharing Your Power

Publicá tu power en un repositorio público de GitHub:

```bash
git init
git add POWER.md mcp.json steering/
git commit -m "Initial release"
git push origin main
```

> El repositorio debe ser **público** para que otros puedan instalarlo. Los repositorios privados requieren que los usuarios tengan permisos de acceso.

Otros pueden instalarlo via **Add power from GitHub** usando la URL de tu repositorio.