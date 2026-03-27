# Crear poderes

> **Fuente:** [kiro.dev/docs/powers/create/](https://kiro.dev/docs/powers/create/)

---

Crea tus propios poderes para extender las capacidades de Kiro con herramientas especializadas, y compartílos con la comunidad.

---

## Lo que necesitas

Todo poder necesita un archivo `POWER.md`. Opcionalmente podés agregar:

- `mcp.json` — Configuración de servidores MCP para integraciones de herramientas
- `steering/` — Archivos de guía específicos por flujo de trabajo

---

## Creando POWER.md

El archivo `POWER.md` tiene dos partes: **frontmatter** e **instrucciones para el agente**.

### Frontmatter: Cuándo activar

El frontmatter le dice a Kiro cuándo cargar tu poder. Usá palabras clave que coinciden con cómo los desarrolladores hablan de tu herramienta.

```yaml
---
name: "supabase"
displayName: "Supabase with local CLI"
description: "Build fullstack applications with Supabase's Postgres database, authentication, storage, and real-time subscriptions"
keywords: ["database", "postgres", "auth", "storage", "realtime", "backend", "supabase", "rls"]
---
```

**Cómo funciona:** Cuando alguien dice "Configuremos la base de datos", Kiro ve "database" en los palabras clave y activa el poder de Supabase. Los MCP tools y la documentación del power se cargan automáticamente en contexto.

### Instrucciones de incorporación

La sección de onboarding corre cuando alguien usa tu poder por primera vez. Usala para validar dependencias, explicar pasos de configuración o crear hooks de espacio de trabajo.

```rebaja
# Incorporación

## Paso 1: Validar el funcionamiento de las herramientas
Antes de usar Supabase Local MCP, asegúrese de que esté instalado lo siguiente:
- **Docker Desktop**: Verificar con: `docker --version`
  - **CRÍTICO**: Si Docker no está instalado o no se está ejecutando, NO continúe.
- **Supabase CLI**: Verificar con: `supabase --version`

## Paso 2: agregar hooks
Agregue un gancho a `.kiro/hooks/review-advisors.kiro.hook`
```

Kiro sigue estas instrucciones automáticamente: verifica que Docker esté corriendo, valida la CLI e instala el gancho de revisión en el espacio de trabajo.

### Instrucciones de dirección

**Enfoque simple** (sin archivos de dirección separados): Incluye toda la guía directamente en `POWER.md` después de la sección de incorporación.

**Enfoque avanzado** (múltiples Steering Files): Para herramientas con muchos flujos de trabajo distintos, mapeá cada flujo de trabajo a un archivo de dirección específico:

```markdown
# When to Load Steering Files
- Setting up a database → `database-setup-workflow.md`
- Writing or formatting SQL code → `supabase-code-format-sql.md`
- Creating or modifying RLS policies → `supabase-database-rls-policies.md`
- Creating PostgreSQL functions → `supabase-database-functions.md`
- Setting up Next.js auth with Supabase SSR → `supabase-nextjs-supabase-auth.md`
- Implementing realtime features → `supabase-use-realtime.md`
```

Esto previene sobrecargar el contexto con todos los patrones de golpe — Kiro carga solo el manejo relevante al flujo de trabajo actual.

---

## Agregar servidores MCP

Si utilizas herramientas MCP, creará un archivo `mcp.json`. Los nombres de servidores deben coincidir con los referenciados en `POWER.md`.

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

> ⚠️ Usamos variables de entorno para claves y secretos API. Durante la instalación, Kiro automáticamente asigna espacios de nombres a los nombres del servidor para evitar conflictos (ej. `supabase-local` → `power-supabase-supabase-local`).

---

## Estructura del directorio

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

## Ejemplos

| Tipo | Estructura |
|---|---|
| **Simple** (archivos de dirección sin) | `POWER.md` + `mcp.json` (opcional) |
| **Con dirección de herramienta única** | `POWER.md` + `mcp.json` + `dirección/schema-patterns.md` |
| **Multiherramienta** | `POWER.md` + `mcp.json` + Múltiples archivos en `steering/` |
| **Solo documentación** | `POWER.md` + `steering/` (sin servidores MCP) |

---

## Pruebas localmente

1. Cree el directorio del power con los archivos necesarios
2. Abrí **Kiro → Panel de poderes → Agregar energía desde la ruta local**
3. Selecciona tu directorio del poder
4. Testeá la activación usando palabras clave de tu power en una conversación

---

## Compartiendo tu poder

Publicá tu power en un repositorio público de GitHub:

```bash
git init
git add POWER.md mcp.json steering/
git commit -m "Initial release"
git push origin main
```

> El repositorio debe ser **público** para que otros puedan instalarlo. Los repositorios privados requieren que los usuarios tengan permisos de acceso.

Otros pueden instalarlo vía **Add power from GitHub** usando la URL de tu repositorio.