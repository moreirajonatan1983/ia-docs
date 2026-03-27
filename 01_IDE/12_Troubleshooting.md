# Solución de problemas

> **Fuente:** [kiro.dev/docs/troubleshooting/](https://kiro.dev/docs/troubleshooting/)

---

## Problemas de instalación de Kiro

### macOS: "Kiro está dañado y no se puede abrir"

Esta ventana emergente es un **falso positivo** en las funciones de seguridad de macOS (Gatekeeper).

**Soluciones (pruebe en orden):**

1. Vaya a **Configuración del sistema → Privacidad y seguridad** y haga clic en **Permitir** o **Abrir de todos modos** para Kiro.
2. Arrastre `Kiro.app` a su escritorio, luego arrástrelo nuevamente a la carpeta Aplicaciones.
3. Reinicie su computadora.
4. Abra Terminal y ejecute:
   ```golpecito
   sudo xattr -d com.apple.quarantine /Aplicaciones/Kiro.app
   ```

---

## Problemas de autenticación

### Fallos de redireccionamiento del navegador durante la autenticación

Si Kiro no te redirige a un navegador durante la autenticación:

**macOS:**
1. Abra Kiro → **Ayuda → Alternar herramientas de desarrollador**
2. Navegue a la pestaña **Consola**
3. Observe cualquier error durante el proceso de inicio de sesión.
4. Verifique que `ioreg` esté en su RUTA:
   ```golpecito
   eco $ RUTA
   cual ioreg
   # Si falta, normalmente se encuentra en /usr/sbin/ioreg
   ```

**Windows:**
1. Abra el símbolo del sistema como administrador
2. Ejecute Kiro con registro:
   ```
   C:\ruta\a\app.exe --enable-logging
   ```
3. Verifique los registros para detectar errores de acceso denegado: asegúrese de que su usuario tenga permisos de administrador

### Problemas del Centro de identidad de AWS IAM

**Se requiere suscripción Q Developer Pro:**
Si ve *"Hubo un error al iniciar sesión"*, asegúrese de tener una suscripción **Q Developer Pro** válida. [Ver estado de suscripción →](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-admin-setup-subscribe-general.html)

**Limitaciones regionales:**
Kiro utiliza de forma predeterminada **Este de EE. UU. (Norte de Virginia)** para la autenticación del Centro de identidad. Si su perfil de Q Developer se encuentra en una región diferente, inicie sesión con Builder ID, Google o GitHub.

**Duración de la sesión y tiempos de espera:**
Las sesiones de Identity Center tienen un tiempo de espera predeterminado de **8 horas**. Los administradores pueden configurar tiempos de espera de sesión más largos en [documentación de AWS →](https://docs.aws.amazon.com/singlesignon/latest/userguide/user-session-duration-how-to-configure.html)

---

## Problemas de integración de Shell

### Solución rápida: "Integración de Shell no disponible"

1. **Actualizar Kiro:** `Cmd+Shift+P` / `Ctrl+Shift+P` → `Kiro: buscar actualizaciones`
2. **Habilitar integración:** `Cmd+Shift+P` / `Ctrl+Shift+P` → `Kiro: Habilitar integración de Shell`
3. **Reiniciar** Kiro

### Instalación manual

Si la configuración automática falla, agregue a su configuración de shell:

**Zsh (`~/.zshrc`):**
```golpecito
[[ "$TERM_PROGRAM" == "kiro" ]] && . "$(kiro --locate-shell-integration-path zsh)"
```

**Bash (`~/.bashrc`):**
```golpecito
[[ "$TERM_PROGRAM" == "kiro" ]] && . "$(kiro --locate-shell-integration-path bash)"
```

**Pescado (`~/.config/fish/config.fish`):**
```pescado
coincidencia de cadena -q "$TERM_PROGRAM" "kiro" y . (kiro --locate-shell-integration-path pez)
```

**PowerShell ($Perfil):**
```powershell
si ($env:TERM_PROGRAM -eq "kiro") { . "$(kiro --locate-shell-integration-path pwsh)" }
```

### Kiro se atasca en el estado "Trabajando..." / Salida del terminal no visible

Causado por personalizaciones del shell que interfieren con la integración del terminal (por ejemplo, `bash-it`, `Oh My Posh`, `Powerlevel10k`).

**Usuarios de Powerlevel10k** — Agregar a `~/.p10k.zsh`:
```golpecito
tipografía -g POWERLEVEL9K_TERM_SHELL_INTEGRATION=true
```

O deshabilite las personalizaciones solo cuando se ejecute dentro de Kiro (`~/.zshrc`):
```golpecito
if [[ "$TERM_PROGRAM" == "kiro" ]]; entonces
  # Dejar vacío
otra cosa
  ZSH_THEME="nivel de potencia10k/nivel de potencia10k"
fi
```

**Usuarios de conchas de pescado** — Actualice el script de integración de conchas para incluir `"kiro"`:

Archivo: `/Applications/Kiro.app/Contents/Resources/app/out/vs/workbench/contrib/terminal/common/scripts/shellIntegration.fish`

Cambiar:
```
coincidencia de cadena --quiet "$TERM_PROGRAM" "vscode"
```
Para:
```
coincidencia de cadena --quiet "$TERM_PROGRAM" "vscode" "kiro"
```

---

## Problemas de Windows

### Actualizaciones deshabilitadas debido a la instalación del administrador

Si Kiro fue instalado por un administrador, es posible que las actualizaciones automáticas estén deshabilitadas. Reinstale Kiro como usuario habitual para restaurar las actualizaciones automáticas.

### No se pueden ejecutar scripts

Habilite la política de ejecución de PowerShell:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### Problema de ruta de OneDrive

Si su perfil de usuario está almacenado en OneDrive, Kiro puede tener dificultades con la resolución de rutas. Mueva su espacio de trabajo de Kiro a una ruta local (fuera de OneDrive) para resolverlo.

---

## Problemas de conexión del servidor MCP

### Problemas comunes

1. **Verificar el estado del servidor** — Abra el panel Kiro → pestaña Servidores MCP → verifique el indicador de estado de la conexión
2. **Verificar configuración**: asegúrese de que `mcp.json` tenga una sintaxis válida y que los comandos/argumentos del servidor sean correctos.
3. **Verifique los requisitos previos**: para el servidor de documentación de AWS, verifique que Python 3.10+ y `uv` estén instalados.
4. **Revisar registros** — Panel de salida → seleccione **"Kiro - Registros de MCP"** en el menú desplegable

### Servidor de documentación de AWS

```golpecito
# Verificar la instalación ultravioleta
uv --versión

# Verificar la versión de Python (se requiere 3.10+)
python3 --versión
```

---

## Obtener ayuda

- [Problemas de GitHub →](https://github.com/kirodotdev)
- [Documentación oficial →](https://kiro.dev/docs/)