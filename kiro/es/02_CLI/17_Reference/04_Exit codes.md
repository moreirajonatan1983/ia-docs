# Códigos de salida

> **Fuente:** [kiro.dev/docs/cli/reference/exit-codes/](https://kiro.dev/docs/cli/reference/exit-codes/)

---

## Referencia del código de salida

| Código | SIGNIFICADO |
|---|---|
| **0** | Éxito — La tarea se completó correctamente |
| **1** | Errores generales |
| **2** | Error de uso / argumentos inválidos |
| **3** | Servidor(es) MCP fallaron al iniciar |

---

## Requerir servidores MCP

Por defecto, los fallos de los servidores MCP se loguean como advertencias **sin afectar el código de salida**. Usaremos `--require-mcp-startup` para fallar inmediatamente cuando los servidores MCP son críticos:

```bash
kiro-cli chat --require-mcp-startup --no-interactive "Run task"
```

Si **cualquier** servidor MCP configurado falla al iniciar, el CLI termina inmediatamente con el código `3`.

> Usá `--require-mcp-startup` en pipelines CI/CD donde las herramientas MCP son esenciales. Esto previene fallas silenciosas donde las tareas se completan sin el utillaje esperado.

---

## Códigos de salida del gancho

Los [Hooks](../03_Chat/../08_Hooks/01_Overview.md) usan un conjunto separado de códigos de salida para controlar la ejecución de herramientas:

| Código | Comportamiento en Hook |
|---|---|
| **0** | Gancho completado exitosamente, continuar |
| **≠ 0** | Hook falló — para hooks `preToolUse`, **bloquea** la ejecución de la herramienta |

---

## Ejemplos de secuencias de comandos

### Script de bash

```golpecito
#!/bin/bash
chat kiro-cli \
  --require-mcp-inicio \
  --no-interactivo \
  --confiar en todas las herramientas \
  "Ejecutar análisis"

código_salida=$?

caso $código_salida en
  0)
    echo " ✅ Éxito "
    ;;
  3)
    echo "❌ Los servidores MCP no pudieron iniciarse"
    salida 1
    ;;
  *)
    echo "❌ Error con el código $exit_code"
    salir $código_salida
    ;;
esac
```

### Canalización de CI/CD (acciones de GitHub)

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

### Canalización de CI/CD (GitLab CI)

```yaml
kiro-analysis:
  script:
    - kiro-cli chat --require-mcp-startup --no-interactive "Run tests"
  allow_failure: false
```

---

## Mejores prácticas

- Usaremos `--require-mcp-startup` en CI/CD cuando tus tareas dependen de las herramientas MCP
- Agregará el registro detallado (`-v` o `-vv`) cuando estés depurando códigos de salida
- Verificará los códigos de salida explícitamente en lugar de depender del comportamiento implícito del shell
- Separar los fallos de MCP de los fallos generales para proporcionar mejores mensajes de error