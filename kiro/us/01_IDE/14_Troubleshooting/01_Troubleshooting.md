# Troubleshooting

> **Source:** [kiro.dev/docs/troubleshooting/](https://kiro.dev/docs/troubleshooting/)

---

## Installation Issues

### macOS: "Kiro is damaged and can't be opened"

Este error es un falso positivo de las features de seguridad de macOS.

**Soluciones:**

1. Ir a **System Settings → Privacy & Security** → clic en **Allow** o **Open anyway** para Kiro
2. Arrastrá `Kiro.app` al escritorio, luego arrastralo del escritorio a la carpeta Applications → reiniciá el sistema
3. Abrí la terminal y ejecutá:
   ```bash
   sudo xattr -d com.apple.quarantine /Applications/Kiro.app
   ```

---

## Authentication Issues

### Browser Redirect Failures During Authentication

**Windows:**
1. Abrí Command Prompt como administrador
2. Ejecutá Kiro con logging habilitado:
   ```
   C:\path\to\app.exe --enable-logging
   ```
3. Revisá los logs en busca de errores
4. Si ves "access denied", verificá que tu usuario tenga permisos de administrador

**macOS:**
1. Abrí Kiro → **Help → Toggle Developer Tools**
2. Navegá a la pestaña **Console**
3. Observá los errores durante el sign-in
4. Problema común: comando `ioreg` faltante en el PATH:
   ```bash
   echo $PATH
   which ioreg
   ```
   Si `ioreg` no aparece, generalmente está en `/usr/sbin/ioreg`

---

### AWS IAM Identity Center Issues

- **`"There was an error signing you in"`:** No tenés una suscripción Q Developer Pro activa — [Ver cómo activar Q Developer Pro →](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-admin-setup-subscribe-general.html)
- **No podés iniciar sesión a pesar de tener credenciales válidas:** Limitación regional — Kiro solo soporta Identity Center en US East (N. Virginia) — Usá Builder ID o login social (Google, GitHub)
- **Sesión expira constantemente:** Timeout por defecto de 8 horas — El administrador puede [configurar sesiones más largas →](https://docs.aws.amazon.com/singlesignon/latest/userguide/user-session-duration-how-to-configure.html)

---

## Shell Integration Issues

La integración de shell conecta Kiro con tu terminal para ejecutar comandos automáticamente y procesar resultados. Sin ella, necesitás copiar y pegar outputs manualmente.

### Quick Fix: "shell integration unavailable"

1. Actualizá Kiro: `Cmd/Ctrl + Shift + P` → **Kiro: Check for Updates**
2. Habilitá la integración: `Cmd/Ctrl + Shift + P` → **Kiro: Enable Shell Integration**
3. Reiniciá Kiro

### Manual Installation

Si la configuración automática falla, agregá a tu shell config:

**Zsh (`~/.zshrc`):**
```bash
[[ "$TERM_PROGRAM" == "kiro" ]] && . "$(kiro --locate-shell-integration-path zsh)"
```

**Bash (`~/.bashrc`):**
```bash
[[ "$TERM_PROGRAM" == "kiro" ]] && . "$(kiro --locate-shell-integration-path bash)"
```

**Fish (`~/.config/fish/config.fish`):**
```fish
string match -q "$TERM_PROGRAM" "kiro" and . (kiro --locate-shell-integration-path fish)
```

**PowerShell (`$Profile`):**
```powershell
if ($env:TERM_PROGRAM -eq "kiro") { . "$(kiro --locate-shell-integration-path pwsh)" }
```

### Kiro Stuck in "Working..." on Terminal Commands

Causado por customizaciones del shell que interfieren con la integración de terminal (ej. bash-it, Oh My Posh, Powerlevel10k).

**Powerlevel10k users:** Agregá a tu `.p10k.zsh`:
```bash
typeset -g POWERLEVEL9K_TERM_SHELL_INTEGRATION=true
```

O deshabilitá los temas dentro de Kiro (`.zshrc`):
```bash
if [[ "$TERM_PROGRAM" == "kiro" ]]; then
  # Leave empty
else
  ZSH_THEME="powerlevel10k/powerlevel10k"
fi
```

**Fish shell users:** Editá el archivo de integración de Kiro:
```
/Applications/Kiro.app/Contents/Resources/app/out/vs/workbench/contrib/terminal/common/scripts/shellIntegration.fish
```
Cambiá la línea que verifica `"vscode"` para incluir también `"kiro"`:
```fish
# Antes:
status is-interactive and string match --quiet "$TERM_PROGRAM" "vscode" and ...
# Después:
status is-interactive and string match --quiet "$TERM_PROGRAM" "vscode" "kiro" and ...
```

---

## Windows Issues

### Updates Disabled Due to Administrator Installation

Si ves este error:
```
Updates are disabled because you are running the user-scope installation of Kiro as Administrator.
```

1. Click derecho en el ícono de Kiro → **Show more options**
2. Seleccioná **Properties** → pestaña **Compatibility**
3. Desmarcá **Run this program as an administrator**
4. Click **Apply** → **OK**

### Unable to Run Scripts (PowerShell 7+)

```powershell
# Verificar política actual
Get-ExecutionPolicy

# Establecer política
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### OneDrive Path Issue

Si usás OneDrive en Windows y el path del escritorio causa problemas:

1. Abrí Command Prompt como administrador
2. Creá un symbolic link:
   ```
   mklink /J "C:\Users\<username>\Desktop" "C:\Users\<username>\OneDrive\Desktop"
   ```
3. Reiniciá el IDE

---

## MCP Server Connection Issues

### Diagnosis Checklist

1. **Estado del server:** Panel de Kiro → pestaña **MCP servers** → verificá el indicador de conexión
2. **Configuración:** Verificá sintaxis JSON en `mcp.json` y que el comando y argumentos sean correctos
3. **Prerrequisitos:** Verificá dependencias instaladas (ej. Python 3.10+ y `uv` para el server de AWS Docs)
4. **Logs:** Output panel → seleccioná **"Kiro - MCP Logs"** → buscá mensajes de error

### AWS Documentation Server

**Fallos de conexión:**
```bash
# Verificar instalación de uv
uv --version

# Verificar versión de Python
python --version

# Probar el server directamente
uvx awslabs.aws-documentation-mcp-server@latest --help
```

**Fallos de búsqueda/lectura:**
- Verificá tu conexión a internet
- Verificá el formato de la URL para páginas de documentación
- Probá con una query más simple

### GitHub MCP Server

**Errores de autenticación:**
- Verificá que tu personal access token es válido
- Asegurate de que el token tiene los scopes requeridos (`repo`, `user`)
- Generá un nuevo token si es necesario

**Rate limiting:**
- GitHub API tiene límites de uso — verificá el estado en los logs de MCP
- Considerá usar un token con mayor límite de rate

---

## Getting Help

Si probaste los pasos anteriores y aún necesitás ayuda:

1. 📋 Revisá las [FAQs](https://kiro.dev/faq) para preguntas comunes
2. 💬 Unite al [Discord de la comunidad](https://discord.gg/kirodotdev) para obtener ayuda
3. 🐛 Enviá un issue en [GitHub](https://github.com/kirodotdev/Kiro/issues) con:
   - Detalles del sistema operativo
   - Versión de Kiro
   - Pasos que ya intentaste
   - Mensajes de error (si aplica)