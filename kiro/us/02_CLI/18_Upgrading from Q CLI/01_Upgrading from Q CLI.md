# Upgrading from Amazon Q Developer CLI

> **Source:** [kiro.dev/docs/cli/migrating-from-q/](https://kiro.dev/docs/cli/migrating-from-q/)

---

## Overview

Kiro CLI es la **próxima evolución de Q CLI**. Tus workflows existentes, suscripción y autenticación continúan funcionando sin ningún cambio.

- Disponible desde el **17 de noviembre de 2025**
- El **24 de noviembre de 2025**, Q Developer CLI con auto-update habilitado se actualizó automáticamente a Kiro CLI
- Si tenías auto-update deshabilitado, actualizá manualmente: `q update` o "Check for updates" en la aplicación Amazon Q

---

## Key Differences

| Característica | Amazon Q Developer CLI | Kiro CLI |
|---|---|---|
| **Nombre del binario** | `q` / `q chat` | `kiro-cli` / `kiro-cli chat` (retrocompatible con `q`) |
| **Autenticación** | Builder ID + IAM Identity Center | Builder ID + IAM Identity Center + **Google + GitHub** |
| **Agente por defecto** | `q_default` | `kiro_default` |
| **Config folder** | `~/.aws/amazonq/` | `~/.kiro/` |
| **Steering/Rules** | `~/.aws/amazonq/rules/` | `~/.kiro/steering/` |
| **Tool names** | `fs_read`, `fs_write`, `execute_bash`, `use_aws`, `report_issue` | `read`, `write`, `shell`, `aws`, `report` (retrocompatibles) |
| **Licencia del software** | Apache 2.0 | AWS Intellectual Property License |
| **Logs** | Varía | `$TMPDIR/kiro-log` |

---

## One-Time Migration During Installation

Al instalar Kiro CLI por primera vez, se ejecuta una **migración automática**:

1. Prompts y agents de `~/.aws/amazonq/` se copian a `~/.kiro/` con los mismos nombres
2. Config MCP de `~/.aws/amazonq/mcp.json` se copia a `~/.kiro/settings/mcp.json` (los conflictos se saltan)  
3. Archivos de `~/.aws/amazonq/rules/` se copian a `~/.kiro/steering/` con los mismos nombres
4. Se crea un `cli.json` con la configuración del Q Developer CLI
5. Kiro CLI **continúa leyendo la carpeta `.amazonq`** en tus proyectos — tus rules, agents y MCP settings existentes siguen funcionando

> Si guardás nuevas configuraciones de prompts o agents, se guardan en la carpeta `.kiro` del proyecto. Si existe ambas carpetas, se lee desde `.kiro`.

---

## Configuration File Paths

| Configuración | Q Developer CLI | Kiro CLI |
|---|---|---|
| MCP (global) | `~/.aws/amazonq/mcp.json` | `~/.kiro/settings/mcp.json` |
| MCP (workspace) | `.amazonq/mcp.json` | `.kiro/settings/mcp.json` |
| Prompts (global) | `~/.aws/amazonq/prompts/` | `~/.kiro/prompts/` |
| Prompts (workspace) | `.amazonq/prompts/` | `.kiro/prompts/` |
| Agents (global) | `~/.aws/amazonq/cli-agents/` | `~/.kiro/agents/` |
| Agents (workspace) | `.amazonq/cli-agents/` | `.kiro/agents/` |
| Steering/Rules (global) | `~/.aws/amazonq/rules/` | `~/.kiro/steering/` |
| Steering/Rules (workspace) | `.amazonq/rules/` | `.kiro/steering/` |
| Settings | — | `~/.kiro/settings/cli.json` |

---

## Important Changes

- **Kiro CLI no modifica tus carpetas `.amazonq` existentes**
- La autenticación y gestión de suscripción usan el **portal web de Kiro**
- Los logs se escriben en `$TMPDIR/kiro-log`
- Los nombres de tools son diferentes pero **retrocompatibles** — tus agents custom existentes siguen funcionando
- El agente por defecto cambió a `kiro_default`. En `/agent list` aparece con "No path found" porque la configuración está en memoria
- El UI tiene colores y nombres actualizados
- El agente por defecto soporta tanto **Amazon Q rules** como **Kiro steering**
- Si tu proyecto tiene ambas carpetas `.kiro` y `.amazonq`, la configuración se carga desde `.kiro` (verás un warning al iniciar sesión)

---

## Frequently Asked Questions

**¿Kiro CLI es retrocompatible con Q Developer CLI?**
Sí. Podés continuar usando los entry points `q` y `q chat`. Toda la funcionalidad de Q Developer CLI está disponible en Kiro CLI.

**¿Tengo que cambiar mis scripts de automatización?**
No. Kiro CLI es retrocompatible. Los viejos nombres de tools (`fs_read`, `fs_write`, etc.) siguen funcionando.

**¿Puedo usar Kiro CLI con mi suscripción Q Developer Pro?**
Sí. Kiro CLI funciona con tu suscripción Q Developer Pro.

**¿Debería migrar a un plan Kiro?**
Kiro ofrece 3 tiers que mejor mapean a las necesidades del developer, y **cada tier soporta overages** — algo que no está disponible en Q Developer Pro.

**¿Kiro usa mi contenido para entrenar modelos?**
Ver [Data Protection →](./16_Privacy%20and%20security/01_Data%20protection.md) y la sección de service improvement.

**¿El output indemnity aplica si actualizo de Q Developer Pro?**
Sí, los suscriptores pagos de Kiro tienen output indemnity, igual que los usuarios Q Developer Pro. Ver Section 50.10 de los Service Terms.

---

## Getting Help

Si encontrás problemas durante la migración:

1. Revisar [CLI Commands Reference →](./17_Reference/01_CLI%20commands.md)
2. Revisar [Troubleshooting →](./15_Troubleshooting.md)
3. Contactar soporte desde el dashboard de Kiro

---

## Next Steps

- [Chat features →](./03_Chat/)
- [Custom Agents →](./04_Custom%20agents/)
- [MCP integration →](./05_MCP/)
- [Agent Hooks →](./07_Hooks.md)
- [Settings Reference →](./17_Reference/05_Settings.md)