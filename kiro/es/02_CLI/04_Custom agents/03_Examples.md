# Ejemplos de agentes

> **Fuente:** [kiro.dev/docs/cli/custom-agents/examples/](https://kiro.dev/docs/cli/custom-agents/examples/)

---

## Agente especialista de AWS

```json
{
  "name": "aws-specialist",
  "description": "Specialized agent for AWS infrastructure management",
  "prompt": "You are an expert AWS infrastructure specialist. Help with CloudFormation, Lambda, S3, EC2, and other AWS services.",
  "tools": ["read", "write", "shell", "aws"],
  "allowedTools": ["read", "aws"],
  "toolsSettings": {
    "aws": {
      "allowedServices": ["s3", "lambda", "cloudformation"],
      "autoAllowReadonly": true
    }
  },
  "resources": ["file://README.md", "file://infrastructure/**/*.yaml"]
}
```

---

## Agente de flujo de trabajo de desarrollo

```json
{
  "name": "dev-workflow",
  "description": "Streamlined development workflow with pre-approved common operations",
  "prompt": "You are a development workflow assistant. Help with coding, testing, and deployment tasks.",
  "tools": ["read", "write", "shell", "@git"],
  "allowedTools": ["read", "@git/git_status", "@git/git_diff", "@git/git_log"],
  "toolsSettings": {
    "shell": {
      "allowedCommands": ["npm test", "npm run build", "git status", "git diff"],
      "autoAllowReadonly": true
    }
  },
  "hooks": {
    "postToolUse": [{ "matcher": "fs_write", "command": "npm run lint --fix" }]
  }
}
```

---

## Agente de revisión de código

```json
{
  "name": "code-reviewer",
  "description": "Focused code review agent with read-only access",
  "prompt": "You are an expert code reviewer. Analyze code for quality, security, performance, and maintainability.",
  "tools": ["read", "@git/git_diff"],
  "allowedTools": ["read", "@git/git_diff"],
  "resources": [
    "file://.kiro/steering/code-standards.md"
  ]
}
```

---

## Agente específico del proyecto

Para un agente específico de proyecto, guárdelo en `.kiro/agents/`:

```json
{
  "name": "my-project-agent",
  "description": "Agent configured for this specific project",
  "prompt": "file://./agent-prompts/project-context.md",
  "tools": ["read", "write", "shell"],
  "allowedTools": ["read"],
  "resources": [
    "file://README.md",
    "file://CONTRIBUTING.md",
    "file://docs/**/*.md",
    "skill://.kiro/skills/**/SKILL.md"
  ],
  "hooks": {
    "agentSpawn": [{ "command": "git status" }]
  }
}
```

---

## Integración remota del servidor MCP

```json
{
  "name": "api-agent",
  "description": "Agent with access to remote API via MCP",
  "mcpServers": {
    "my-api": {
      "type": "http",
      "url": "https://api.example.com/mcp"
    }
  },
  "tools": ["read", "@my-api"],
  "allowedTools": ["read", "@my-api/get_data"]
}
```

### Con configuración OAuth

```json
{
  "name": "oauth-agent",
  "mcpServers": {
    "secure-api": {
      "type": "http",
      "url": "https://secure-api.example.com/mcp",
      "oauth": {
        "redirectUri": "127.0.0.1:8080",
        "oauthScopes": ["read", "write"]
      }
    }
  }
}
```

---

## Consejos para crear agentes personalizados eficaces

1. **Defina el alcance claramente** — Utilice `tools` y `allowedTools` para limitar exactamente qué puede hacer el agente
2. **Aprovechá los recursos** — Incluí documentación relevante del proyecto en `resources`
3. **Usá hooks para automatización** — `postToolUse` es ideal para formatear código automáticamente
4. **Comenzá simple** — Creá un agente básico y ampliará sus capacidades según sea necesario
5. **Compartí con el equipo** — Almacená agentes de equipo en `.kiro/agents/` y cometeá al repositorio