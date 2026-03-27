# Agent Skills

> **Source:** [kiro.dev/docs/skills/](https://kiro.dev/docs/skills/)

---

## What Are Skills?

Las **Skills** son paquetes de instrucciones portables que siguen el estándar abierto [Agent Skills](https://agentskills.io). Agrupan instrucciones, scripts y templates en paquetes reutilizables que Kiro puede activar cuando son relevantes para tu tarea.

Kiro soporta el estándar Agent Skills, por lo que podés:
- Importar skills de la comunidad o de otras herramientas de IA compatibles
- Compartir tus propias skills en el ecosistema

---

## How Skills Work

Las skills resuelven el problema del contexto excesivo usando **progressive disclosure**:

| Etapa | Descripción |
|---|---|
| **1. Discovery** | Al inicio, Kiro carga solo el nombre y descripción de cada skill |
| **2. Activation** | Cuando tu request coincide con la descripción de una skill, Kiro carga las instrucciones completas |
| **3. Execution** | Kiro sigue las instrucciones, cargando scripts o archivos de referencia solo cuando es necesario |

Esto mantiene el contexto enfocado mientras da a Kiro acceso a conocimiento especializado extenso bajo demanda.

---

## Using Skills

Kiro activa automáticamente las skills cuando tu request coincide con su descripción.

También podés invocar una skill directamente:
- Escribí `/` en el chat → los skills disponibles aparecen como slash commands
- Seleccioná un slash command → carga las instrucciones completas del skill

Gestioná tus skills desde la sección **Agent Steering & Skills** en el panel de Kiro.

---

## Skill Scope

| Scope | Ubicación | Uso |
|---|---|---|
| **Workspace** | `.kiro/skills/` | Solo el proyecto actual. Skills para workflows específicos del proyecto (deployment, convenciones del equipo) |
| **Global** | `~/.kiro/skills/` | Disponible en todos los workspaces. Skills personales usadas en cualquier proyecto (code review, documentación) |

> En caso de conflicto de nombres entre skills global y workspace, Kiro **prioriza el workspace skill**. Esto permite definir skills globales con posibilidad de sobreescribirlas por proyecto.

---

## Importing Skills

1. Abrí la sección **Agent Steering & Skills** en el panel de Kiro
2. Hacé click en **+** y seleccioná **Import a skill**
3. Elegí el origen:
   - **GitHub** — Importá desde una URL de repositorio público (apuntando a la carpeta del skill o directamente al `SKILL.md`). La URL debe apuntar a un subdirectorio, no a la raíz del repositorio
   - **Local folder** — Importá desde tu filesystem

> Los skills importados se copian a tu directorio de skills y funcionan de inmediato.

---

## Creating a Skill

Un skill es una carpeta que contiene un archivo `SKILL.md`:

```
my-skill/
├── SKILL.md          # Requerido
├── scripts/          # Opcional — código ejecutable
├── references/       # Opcional — documentación
└── assets/           # Opcional — templates
```

### SKILL.md Format

```markdown
---
name: pr-review
description: Review pull requests for code quality, security issues, and test coverage.
             Use when reviewing PRs or preparing code for review.
---

## Review process
1. Check for security vulnerabilities
2. Verify error handling
3. Confirm test coverage
4. Review naming and structure
```

### Frontmatter Fields

| Campo | Descripción |
|---|---|
| `name` | Identificador del skill (usado como slash command) |
| `description` | Cuándo activar el skill — debe ser precisa y específica |
| `license` | Licencia del skill (para distribución) |
| `compatibility` | Herramientas AI compatibles |
| `metadata` | Metadatos adicionales |

Ver la [especificación completa →](https://agentskills.io/specification)

---

## How Skills Differ from Steering and Powers

- **Skills** are portable packages following an open standard. They load on-demand and can include scripts. Use for reusable workflows you want to share or import from others.
- **Steering** is Kiro-specific context that shapes agent behavior. It supports `always`, `auto`, `fileMatch`, and `manual` modes. Use for project standards and conventions.
- **Powers** bundle MCP tools with knowledge and workflows. They activate dynamically based on context. Use for integrations where you need both tools and guidance.

> **Tip:** For MCP integrations, [powers](https://kiro.dev/docs/powers) are usually a better fit—they bundle tools with built-in guidance and activate automatically based on what you're working on.

---

## Best Practices

- **Descripciones precisas** — Kiro las usa para decidir cuándo activar. Incluí keywords específicas: `"Review pull requests for security and test coverage"` > `"helps with code review"`
- **SKILL.md enfocado** — Poné documentación detallada en archivos `references/`. Kiro carga el SKILL.md completo en la activación
- **Scripts para tareas determinísticas** — Validación, generación de archivos y llamadas a APIs funcionan mejor como scripts que como código generado por LLM
- **Elegí el scope correcto** — Global para workflows personales; workspace para procedimientos del equipo

---

## Related

- [Steering →](./03_Steering.md)
- [Powers →](./06_Powers/01_Install%20powers.md)
- [Agent Skills specification →](https://agentskills.io/specification)