# Agent Skills

> **Source:** [kiro.dev/docs/cli/skills/](https://kiro.dev/docs/cli/skills/)

---

Los Agent Skills son paquetes portables de instrucciones que se activan automáticamente cuando tu request coincide con su descripción. Son similares a los steering files pero **on-demand** — Kiro solo los carga cuando son necesarios.

---

## How Skills Work

Al iniciar una sesión de chat, Kiro descubre los skills disponibles leyendo sus nombres y descripciones. Cuando tu request coincide con la descripción de un skill, Kiro carga automáticamente las instrucciones completas y las sigue.

```
> Review this PR for security issues
[skill: pr-review activated]
I'll review the PR using the security checklist...
```

Los skills **se activan automáticamente** según tu request. No hay slash command para invocarlos — Kiro decide cuándo un skill es relevante comparando tu request contra las descripciones de los skills.

Para ver qué skills están disponibles en tu sesión actual:

```
> /context show
```

---

## Skill Locations

Los skills pueden almacenarse en dos lugares:

| Ubicación | Alcance |
|---|---|
| `.kiro/skills/` | **Workspace** — Solo para ese proyecto |
| `~/.kiro/skills/` | **Global** — Disponible en todos los workspaces |

Cuando skills comparten el mismo nombre, **los workspace skills tienen prioridad** sobre los globales.

### Default Agent

El agente por defecto (`kiro_default`) carga automáticamente todos los skills en `.kiro/skills/` y `~/.kiro/skills/`.

### Custom Agents

Los custom agents requieren que especifiques explícitamente los skills en su configuración usando el protocolo `skill://`:

```json
{
  "resources": ["skill://pr-review", "skill://cdk-deploy"]
}
```

---

## Creating a Skill

Un skill es una **carpeta** que contiene un archivo `SKILL.md`:

```
pr-review/
├── SKILL.md         # Requerido
└── references/      # Opcional
    └── checklist.md
```

### SKILL.md Format

El archivo empieza con **YAML frontmatter** seguido de instrucciones en Markdown:

```markdown
---
name: pr-review
description: Review pull requests for code quality, security issues, and test coverage. Use when reviewing PRs or preparing code for review.
---

## Review checklist
When reviewing a pull request:
1. Check for vulnerabilities, injection risks, exposed secrets
2. Verify edge cases and failure modes are handled
3. Confirm new code has appropriate tests
4. Ensure variables and functions have clear names

## Common issues to flag
- Hardcoded credentials or API keys
- Missing input validation
- Unhandled promise rejections
- Console.log statements left in production code
```

### Frontmatter Fields

| Campo | Descripción |
|---|---|
| `name` | Identificador único del skill |
| `description` | **Crítico** — Determina cuándo se activa. Incluir keywords y acciones específicas. |

### Reference Files

Para documentación extensa, usá una carpeta `references/`:

```
aws-deployment/
├── SKILL.md
└── references/
    ├── ecs-guide.md
    └── troubleshooting.md
```

Referenciá los archivos desde `SKILL.md`:

```markdown
For ECS deployments, follow the guide in `references/ecs-guide.md`.
```

Kiro carga los archivos de referencia **solo cuando las instrucciones lo indican**.

---

## Full Example — CDK Deploy Skill

```
cdk-deploy/
├── SKILL.md
└── references/
    └── stack-patterns.md
```

**SKILL.md:**
```markdown
---
name: cdk-deploy
description: Deploy AWS CDK stacks with best practices. Use when deploying infrastructure, running cdk deploy, or troubleshooting CDK issues.
---

## Deployment workflow
1. Run `cdk synth` to validate templates before deploying
2. Use `cdk diff` to preview what will change
3. Run `cdk deploy` and review IAM changes

## Pre-deployment checks
- Verify AWS credentials are configured for the target account
- Check that the CDK version matches the project's requirements
- Review `references/stack-patterns.md` for environment-specific patterns

## Rollback procedure
If deployment fails:
1. Check CloudFormation console for the specific error
2. Run `cdk destroy` only if the stack is in a failed state
3. Fix the issue and redeploy
```

**Uso:**
```
> Deploy my CDK stack to staging
[skill: cdk-deploy activated]
I'll follow the deployment workflow. First, let me synthesize the templates...
```

---

## Best Practices

- **Descripciones precisas** — La description determina la activación. Ejemplos:
  - ✅ `Review pull requests for security vulnerabilities. Use when reviewing PRs.`
  - ❌ `Helps with code review`
- **SKILL.md accionable** — Poné el material de referencia detallado en `references/`
- **Elegí el scope correcto** — Skills globales para workflows personales; workspace para procedimientos de equipo
- **Versión de control** — Commitá `.kiro/skills/` a tu repo para que todo el equipo comparta los workflows

---

## Related

- [Steering →](./06_Steering.md) — Contexto y convenciones del proyecto
- [Custom Agents →](./04_Custom%20agents/) — Configuración de agentes y recursos
- [ACP →](./08_ACP.md) — Agent Client Protocol