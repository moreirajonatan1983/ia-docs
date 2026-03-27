# Solución de problemas

> **Fuente:** [kiro.dev/docs/troubleshooting/](https://kiro.dev/docs/troubleshooting/)

---

## Problemas de instalación

### macOS: "Kiro está dañado y no se puede abrir"

Este error es un falso positivo de las funciones de seguridad de macOS.

**Soluciones:**

1. Vaya a **Configuración del sistema → Privacidad y seguridad** → haga clic en **Permitir** o **Abrir de todos modos** para Kiro
2. Arrastrará `Kiro.app` al escritorio, luego arrastralo del escritorio a la carpeta Aplicaciones → reiniciará el sistema
3. Abrí la terminal y ejecutá:
   ```golpecito
   sudo xattr -d com.apple.quarantine /Aplicaciones/Kiro.app
   ```

---

## Problemas de autenticación

### Fallos de redireccionamiento del navegador durante la autenticación

**Windows:**
1. Abra el símbolo del sistema como administrador
2. Ejecutá Kiro con logging habilitado:
   ```
   C:\ruta\a\app.exe --enable-logging
   ```
3. Revisá los logs en busca de errores
4. Si ves "acceso denegado", verificará que tu usuario tiene permisos de administrador

**macOS:**
1. Abrí Kiro → **Ayuda → Alternar herramientas de desarrollador**
2. Navegá a la pestaña **Consola**
3. Observará los errores durante el inicio de sesión
4. Problema común: comando `ioreg` faltante en el PATH:
   ```golpecito
   eco $ RUTA
   cual ioreg
   ```
   Si `ioreg` no aparece, generalmente está en `/usr/sbin/ioreg`

---

### Problemas del Centro de identidad de AWS IAM

| Error | causa | Solución |
|---|---|---|
| `"Hubo un error al iniciar sesión"` | No tienes una suscripción Q Developer Pro activa | [Ver cómo activar Q Developer Pro →](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-admin-setup-subscribe-general.html) |
| No podés iniciar sesión a pesar de tener credenciales válidas | Limitación regional — Kiro solo soporta Identity Center en US East (N. Virginia) | Utilice Builder ID para iniciar sesión en redes sociales (Google, GitHub) |
| Sesión expira constantemente | Timeout por defecto de 8 horas | El administrador puede [configurar sesiones más largas →](https://docs.aws.amazon.com/singlesignon/latest/userguide/user-session-duration-how-to-configure.html) |

---

## Problemas de integración de Shell

La integración de shell conecta Kiro con tu terminal para ejecutar comandos automáticamente y procesar resultados. Sin ella, necesitarás copiar y pegar las salidas manualmente.

### Solución rápida: "integración de shell no disponible"

1. Actualizá Kiro: `Cmd/Ctrl + Shift + P` → **Kiro: Buscar actualizaciones**
2. Habilitará la integración: `Cmd/Ctrl + Shift + P` → **Kiro: Habilitar integración de Shell**
3. Reinicia Kiro

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

### Kiro se atasca en "Trabajando..." en los comandos de la terminal

Causado por personalizaciones del shell que interfieren con la integración de terminal (ej. bash-it, Oh My Posh, Powerlevel10k).

**Usuarios de Powerlevel10k:** Agrega a tu `.p10k.zsh`:
```golpecito
tipografía -g POWERLEVEL9K_TERM_SHELL_INTEGRATION=true
```

O deshabilitará los temas dentro de Kiro (`.zshrc`):
```golpecito
if [[ "$TERM_PROGRAM" == "kiro" ]]; entonces
  # Dejar vacío
otra cosa
  ZSH_THEME="nivel de potencia10k/nivel de potencia10k"
fi
```

**Usuarios de conchas de pescado:** Editá el archivo de integración de Kiro:
```
/Aplicaciones/Kiro.app/Contents/Resources/app/out/vs/workbench/contrib/terminal/common/scripts/shellIntegration.fish
```
Cambiá la línea que verifica `"vscode"` para incluir también `"kiro"`:
```pescado
#Antes:
el estado es interactivo y la cadena coincide: silencioso "$TERM_PROGRAM" "vscode" y...
#Después:
el estado es interactivo y la cadena coincide: silencioso "$TERM_PROGRAM" "vscode" "kiro" y ...
```

---

## Problemas de Windows

### Actualizaciones deshabilitadas debido a la instalación del administrador

Si ves este error:
```
Las actualizaciones están deshabilitadas porque está ejecutando la instalación de Kiro en el ámbito del usuario como administrador.
```

1. Haz clic en derecho en el ícono de Kiro → **Mostrar más opciones**
2. Seleccioná **Propiedades** → pestaña **Compatibilidad**
3. Desmarcar **Ejecuta este programa como administrador**
4. Haga clic en **Aplicar** → **Aceptar**

### No se pueden ejecutar scripts (PowerShell 7+)

```powershell
# Verificar política actual
Get-ExecutionPolicy

# Establecer política
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### Problema de ruta de OneDrive

Si usa OneDrive en Windows y la ruta del escritorio causa problemas:

1. Abra el símbolo del sistema como administrador
2. Crea un enlace simbólico:
   ```
   mklink /J "C:\Users\<nombre de usuario>\Desktop" "C:\Users\<nombre de usuario>\OneDrive\Desktop"
   ```
3. Reiniciá el IDE

---

## Problemas de conexión del servidor MCP

### Lista de verificación de diagnóstico

1. **Estado del servidor:** Panel de Kiro → pestaña **MCP servers** → verificará el indicador de conexión
2. **Configuración:** Verificá sintaxis JSON en `mcp.json` y que el comando y argumentos sean correctos
3. **Prerrequisitos:** Verifique las dependencias instaladas (ej. Python 3.10+ y `uv` para el servidor de AWS Docs)
4. **Registros:** Panel de salida → seleccioná **"Kiro - MCP Logs"** → buscá mensajes de error

### Servidor de documentación de AWS

**Fallo de conexión:**
```golpecito
# Verificar instalación de uv
uv --versión

# Verificar versión de Python
Python --versión

# Probar el servidor directamente
uvx awslabs.aws-documentation-mcp-server@latest --ayuda
```

**Fallos de búsqueda/lectura:**
- Verifica tu conexión a internet
- Verifique el formato de la URL para páginas de documentación
- Probá con una consulta más sencilla

### Servidor MCP de GitHub

**Errores de autenticación:**
- Verifica que tu token de acceso personal es válido
- Asegurate de que el token tiene los alcances requeridos (`repo`, `user`)
- Generará un nuevo token si es necesario

**Límite de tasa:**
- GitHub API tiene límites de uso: verificará el estado en los registros de MCP
- Considerá usar un token con mayor límite de tasa

---

## Obtener ayuda

Si probaste los pasos anteriores y aún necesitas ayuda:

1. 📋 Revisa las [FAQs](https://kiro.dev/faq) para preguntas comunes
2. 💬 Unite al [Discord de la comunidad](https://discord.gg/kirodotdev) para obtener ayuda
3. 🐛 Enviá un problema en [GitHub](https://github.com/kirodotdev/Kiro/issues) con:
   - Detalles del sistema operativo
   - Versión de Kiro
   - Pasos que ya intentaste
   - Mensajes de error (si aplica)