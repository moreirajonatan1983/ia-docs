# Exit Codes

> **Source:** [kiro.dev/docs/cli/reference/exit-codes/](https://kiro.dev/docs/cli/reference/exit-codes/)

---

## Exit Code Reference

| Código | Significado |
|---|---|
| **0** | Éxito — La tarea se completó correctamente |
| **1** | Error general |
| **2** | Error de uso / argumentos inválidos |
| **3** | MCP server(s) fallaron al iniciar |

---

## Requiring MCP Servers

Por defecto, los fallos de MCP servers se loguean como warnings **sin afectar el exit code**. Usá `--require-mcp-startup` para fallar inmediatamente cuando los MCP servers son críticos:

```bash
kiro-cli chat --require-mcp-startup --no-interactive "Run task"
```

Si **cualquier** servidor MCP configurado falla al iniciar, el CLI termina inmediatamente con código `3`.

> Usá `--require-mcp-startup` en CI/CD pipelines donde las tools MCP son esenciales. Esto previene fallas silenciosas donde las tareas se completan sin el tooling esperado.

---

## Hook Exit Codes

Los [Hooks](../03_Chat/../08_Hooks/01_Overview.md) usan un conjunto separado de exit codes para controlar la ejecución de tools:

| Código | Comportamiento en Hook |
|---|---|
| **0** | Hook completado exitosamente, continuar |
| **≠ 0** | Hook falló — para hooks `preToolUse`, **bloquea** la ejecución de la tool |

---

## Scripting Examples

### Bash Script

```bash
#!/bin/bash
kiro-cli chat \
  --require-mcp-startup \
  --no-interactive \
  --trust-all-tools \
  "Run analysis"

exit_code=$?

case $exit_code in
  0)
    echo "✅ Success"
    ;;
  3)
    echo "❌ MCP servers failed to start"
    exit 1
    ;;
  *)
    echo "❌ Failed with code $exit_code"
    exit $exit_code
    ;;
esac
```

### CI/CD Pipeline (GitHub Actions)

```yaml
- name: Run Kiro task
  run: |
    kiro-cli chat \
      --require-mcp-startup \
      --no-interactive \
      --trust-all-tools \
      "Analyze code quality"
  continue-on-error: false
```

### CI/CD Pipeline (GitLab CI)

```yaml
kiro-analysis:
  script:
    - kiro-cli chat --require-mcp-startup --no-interactive "Run tests"
  allow_failure: false
```

---

## Best Practices

- Usá `--require-mcp-startup` en CI/CD cuando tus tareas dependen de MCP tools
- Agregá verbose logging (`-v` o `-vv`) cuando estés debuggeando exit codes
- Verificá exit codes explícitamente en lugar de depender del comportamiento implícito del shell
- Separar los fallos de MCP de los fallos generales para proveer mejores mensajes de error