# Actualización desde la CLI para desarrolladores de Amazon Q

> **Fuente:** [kiro.dev/docs/cli/migrating-from-q/](https://kiro.dev/docs/cli/migrating-from-q/)

---

## Descripción general

Kiro CLI es la **próxima evolución de Q CLI**. Tus flujos de trabajo existentes, suscripción y autenticación continúan funcionando sin ningún cambio.

- Disponible desde el **17 de noviembre de 2025**
- El **24 de noviembre de 2025**, Q Developer CLI con actualización automática habilitada se actualizó automáticamente a Kiro CLI
- Si tenías la actualización automática deshabilitada, actualizá manualmente: `q update` o "Check for update" en la aplicación Amazon Q

---

## Diferencias clave

| Característica | CLI para desarrolladores de Amazon Q | Kiro CLI |
|---|---|---|
| **Nombre del binario** | `q` / `q chat` | `kiro-cli` / `kiro-cli chat` (retrocompatible con `q`) |
| **Autenticación** | ID de constructor + Centro de identidad IAM | ID de constructor + Centro de identidad IAM + **Google + GitHub** |
| **Agente por defecto** | `q_default` | `kiro_default` |
| **Carpeta de configuración** | `~/.aws/amazonq/` | `~/.kiro/` |
| **Dirección/Reglas** | `~/.aws/amazonq/rules/` | `~/.kiro/dirección/` |
| **Nombres de herramientas** | `fs_read`, `fs_write`, `execute_bash`, `use_aws`, `report_issue` | `leer`, `escribir`, `shell`, `aws`, `report` (retrocompatibles) |
| **Licencia del software** | Apache 2.0 | Licencia de propiedad intelectual de AWS |
| **Registros** | Varia | `$TMPDIR/kiro-log` |

---

## Migración única durante la instalación

Al instalar Kiro CLI por primera vez, se ejecuta una **migración automática**:

1. Prompts y agentes de `~/.aws/amazonq/` se copian a `~/.kiro/` con los mismos nombres
2. Configure MCP de `~/.aws/amazonq/mcp.json` se copia a `~/.kiro/settings/mcp.json` (los conflictos se saltan)  
3. Archivos de `~/.aws/amazonq/rules/` se copian a `~/.kiro/steering/` con los mismos nombres
4. Se crea un `cli.json` con la configuración de Q Developer CLI
5. Kiro CLI **continúa leyendo la carpeta `.amazonq`** en tus proyectos — tus reglas, agentes y configuraciones de MCP existentes siguen funcionando

> Si guardas nuevas configuraciones de avisos o agentes, se guardan en la carpeta `.kiro` del proyecto. Si existen ambas carpetas, lee desde `.kiro`.

---

## Rutas del archivo de configuración

| Configuración | CLI de desarrollador Q | Kiro CLI |
|---|---|---|
| PCM (global) | `~/.aws/amazonq/mcp.json` | `~/.kiro/settings/mcp.json` |
| MCP (espacio de trabajo) | `.amazonq/mcp.json` | `.kiro/settings/mcp.json` |
| Avisos (globales) | `~/.aws/amazonq/prompts/` | `~/.kiro/prompts/` |
| Mensajes (espacio de trabajo) | `.amazonq/prompts/` | `.kiro/prompts/` |
| Agentes (globales) | `~/.aws/amazonq/cli-agents/` | `~/.kiro/agents/` |
| Agentes (espacio de trabajo) | `.amazonq/cli-agents/` | `.kiro/agentes/` |
| Dirección/Reglas (global) | `~/.aws/amazonq/rules/` | `~/.kiro/dirección/` |
| Dirección/Reglas (espacio de trabajo) | `.amazonq/rules/` | `.kiro/dirección/` |
| Configuración | — | `~/.kiro/settings/cli.json` |

---

## Cambios importantes

- **Kiro CLI no modifica tus carpetas `.amazonq` existentes**
- La autenticación y gestión de suscripción usan el **portal web de Kiro**
- Los registros se escriben en `$TMPDIR/kiro-log`
- Los nombres de herramientas son diferentes pero **retrocompatibles** — tus agentes personalizados existentes siguen funcionando
- El agente por defecto cambió a `kiro_default`. En `/agent list` aparece con "No se encontró ruta" porque la configuración está en memoria
- La interfaz de usuario tiene colores y nombres actualizados.
- El agente por defecto soporta tanto **Amazon Q Rules** como **Kiro Steering**
- Si tu proyecto tiene ambas carpetas `.kiro` y `.amazonq`, la configuración se carga desde `.kiro` (verás una advertencia al iniciar sesión)

---

## Preguntas frecuentes

**¿Kiro CLI es retrocompatible con Q Developer CLI?**
Sí. Podés continuar usando los puntos de entrada `q` y `q chat`. Toda la funcionalidad de Q Developer CLI está disponible en Kiro CLI.

**¿Tengo que cambiar mis scripts de automatización?**
No. Kiro CLI es retrocompatible. Los viejos nombres de herramientas (`fs_read`, `fs_write`, etc.) siguen funcionando.

**¿Puedo usar Kiro CLI con mi suscripción Q Developer Pro?**
Sí. Kiro CLI funciona con tu suscripción Q Developer Pro.

**¿Deberías migrar a un plan Kiro?**
Kiro ofrece 3 niveles que mejor mapean a las necesidades del desarrollador, y **cada nivel soporta excedentes** — algo que no está disponible en Q Developer Pro.

**¿Kiro usa mi contenido para entrenar modelos?**
Ver [Protección de datos →](./16_Privacy%20and%20security/01_Data%20protection.md) y la sección de mejora del servicio.

**¿La aplicación de indemnización de salida se actualiza de Q Developer Pro?**
Sí, los suscriptores de pagos de Kiro tienen indemnización de salida, igual que los usuarios de Q Developer Pro. Ver Sección 50.10 de los Términos de Servicio.

---

## Obtener ayuda

Si encuentras problemas durante la migración:

1. Revisar [Referencia de comandos CLI →](./17_Reference/01_CLI%20commands.md)
2. Revisar [Solución de problemas →](./15_Troubleshooting.md)
3. Contactar soporte desde el tablero de Kiro

---

## Próximos pasos

- [Funciones de chat →](./03_Chat/)
- [Agentes personalizados →](./04_Custom%20agents/)
- [Integración MCP →](./05_MCP/)
- [Agente Hooks →](./07_Hooks.md)
- [Referencia de configuración →](./17_Reference/05_Settings.md)