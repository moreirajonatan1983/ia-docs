# Gestión de permisos de herramientas

> **Fuente:** [kiro.dev/docs/cli/chat/permissions/](https://kiro.dev/docs/cli/chat/permissions/)

---

Kiro CLI utiliza un sistema de permisos granular que le permite controlar exactamente qué herramientas pueden ejecutarse automáticamente y cuáles requieren su aprobación cada vez.

---

## Comandos de herramientas

| Comando | Acción |
|---|---|
| `/herramientas` | Ver el estado de los permisos para todas las herramientas actuales |
| `/tools confianza <herramienta>` | Confíe en una herramienta específica para la sesión actual |
| `/tools no es de confianza <herramienta>` | Desconfiar de una herramienta específica para la sesión actual |
| `/tools confianza-todo` | Confíe en todas las herramientas a la vez (úselas con precaución) |
| `/restablecer herramientas` | Restablecer permisos a los valores predeterminados |

```bash
$ kiro-cli chat
Kiro> /tools
Kiro> /tools trust read
Kiro> /tools untrust shell
Kiro> /tools trust-all
```

**Estados de permiso:**
- **Confiable**: Kiro puede usar la herramienta sin pedir commit
- **Por solicitud** — Kiro debe solicitar tu commit cada vez

> ⚠️ `/tools trust-all` conlleva riesgos de seguridad. Consulte [Usar /tools trust-all de forma segura](https://kiro.dev/docs/cli/chat/security/#using-tools-trust-all-safely).

---

## Herramientas disponibles

| Herramienta | Descripción |
|---|---|
| `leer` | Leer archivos y directorios |
| `escribir` | Crear y editar archivos |
| `cáscara` | Ejecutar comandos bash |
| `aws` | Integración de la CLI de AWS |
| `informe` | Información del informe |

---

## Niveles de confianza del comando Shell

Cuando Kiro solicita ejecutar un comando de shell, obtienes un **selector de confianza escalonado** en lugar de todo o nada:

```
Press (↑↓) to navigate (⏎) to select scope
> Full command    → git pull --rebase
  Partial command → git pull *
  Base command    → git *
  Entire Tool     → *
```

**Niveles de confianza (más → menos restrictivos):**

| Nivel | Ejemplo | Cubiertas |
|---|---|---|
| Comando completo | `git pull --rebase` | Sólo este comando exacto |
| Comando parcial | `git pull *` | Cualquier variante de `git pull` |
| Comando base | `git *` | Todos los comandos de git |
| Herramienta completa | `*` | Todos los comandos del shell |

Después de seleccionar, Kiro confirma: ` ✓ Confiable: git pull --rebase`

Los patrones confiables persisten durante la sesión y se almacenan como expresiones regulares en "allowedCommands".

> Si un comando coincide con un patrón `deniedCommands`, las opciones granulares no están disponibles; solo permita una vez o confíe en toda la herramienta.

---

## Niveles de confianza de ruta de lectura y escritura

Cuando Kiro accede a archivos **fuera del directorio de trabajo actual**, obtienes un selector de ruta específica:

```
Press (↑↓) to navigate (⏎) to select scope
> Specific paths    → ~/.config/app/settings.json
  Complete directory → ~/.config/app
  Entire Tool        → *
```

> Las rutas **dentro** del directorio de trabajo actual NO activan el selector.