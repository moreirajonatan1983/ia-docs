# Solución de problemas: Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/troubleshooting/](https://kiro.dev/docs/cli/troubleshooting/) | [kiro.dev/docs/cli/reference/cli-commands/](https://kiro.dev/docs/cli/reference/cli-commands/)

---

## Herramientas de diagnóstico

### Diagnóstico automático

```bash
kiro-cli doctor          # Diagnóstico estándar
kiro-cli doctor --all    # Todos los checks disponibles
kiro-cli doctor --strict # Modo estricto (falla en warnings)
```

### Informe completo del sistema

```bash
kiro-cli diagnostic
kiro-cli diagnostic --format json-pretty   # Output estructurado
kiro-cli diagnostic --force                # Sin requerir que la app esté corriendo
```

### Registros de Debug

```bash
kiro-cli --verbose chat "..."    # -v / -vv / -vvv para más detalle
kiro-cli diagnostic              # Ver versión, OS, env vars, paths
```

### Volcado de registros para soporte

Desde el chat:
```
> /logdump # Registros de chat
> /logdump --mcp # Chat + registros del servidor MCP
```
Cree un archivo `q-logs-YYYY-MM-DDTHH-MM-SSZ.zip` en el directorio actual.

---

## Problemas de autenticación

### Error "Ya he iniciado sesión"

```bash
kiro-cli logout
kiro-cli login
```

### El navegador no se abre (SSH/Remoto)

```golpecito
inicio de sesión de kiro-cli --use-device-flow
```
Muestra un código de dispositivo y URL para autenticar desde otro dispositivo.

### La autenticación del Centro de identidad falla

Verifica con tu administrador:
- URL correcta del Centro de Identidad
- Región AWS correcta
- Permisos IAM asignados

```bash
kiro-cli login --license pro \
  --identity-provider https://my-org.awsapps.com/start \
  --region us-east-1
```

### Ver usuario actual

```bash
kiro-cli whoami
kiro-cli whoami --format json-pretty
```

---

## Problemas de instalación

### Comando `kiro-cli` no encontrado

```golpecito
cual kiro-cli
# Verificar que la ruta esté en $PATH

# Agregar al .zshrc / .bashrc:
exportar RUTA="$HOME/.local/bin:$RUTA"
```

### Actualizar a la última versión

```bash
kiro-cli update
kiro-cli update --non-interactive
```

### Reinstalar integraciones

```bash
kiro-cli integrations reinstall
kiro-cli integrations status
```

---

## Problemas de chat/conectividad

### Red/Proxy

```golpecito
exportar HTTPS_PROXY=http://proxy.company.com:8080
exportar NO_PROXY=localhost,127.0.0.1

# Verificar conectividad
rizo -v https://api.kiro.dev/health
```

### Tiempo de espera de API

```bash
kiro-cli settings api.timeout 60    # Aumentar a 60s (default: 30s)
```

### Ventana contextual llena

Kiro compacta automáticamente el contexto. Para hacerlo manualmente:
```
> /compacto
```

---

## Problemas con el servidor MCP

### Servidor MCP no iniciado

```golpecito
# Ver estado de servidores MCP
lista de mcp de kiro-cli
estado de kiro-cli mcp --nombre mi-servidor

# Verificar en el chat
> /mcp

# Forzar fallo si MCP es crítico
chat de kiro-cli --require-mcp-startup ...
```

### Registros de servidores MCP

```
> /logdump --mcp
```

### Tiempo de espera de inicialización

```bash
kiro-cli settings mcp.initTimeout 30    # Aumentar timeout (default: 10s)
```

---

## Problemas con el agente personalizado

### Agente no se carga

```bash
kiro-cli agent list             # Verificar que aparece en la lista
kiro-cli agent validate         # Validar configuración JSON
kiro-cli agent edit my-agent    # Editar y corregir
```

### Errores de JSON en configuración

```bash
# Validar JSON manualmente
cat ~/.kiro/agents/my-agent.json | python3 -m json.tool
```

Ver [Solución de problemas de agentes personalizados →](./04_Custom%20agents/04_Troubleshooting.md) para errores específicos.

---

## Problemas de inteligencia de código

### LSP no responde

```bash
> /code init -f    # Forzar reinicialización
> /code status     # Ver estado del servidor LSP
> /code logs       # Ver logs de LSP
```

---

## Problemas de autocompletar

### Autocompletado no funciona

```bash
kiro-cli doctor    # Verificar instalación
# Reiniciar terminal después de instalación
# Verificar integración en .bashrc / .zshrc
```

### Sugerencias en línea deshabilitadas

```bash
kiro-cli inline enable
kiro-cli inline status
```

---

## Problemas de notificación

### Crear un problema de soporte

```bash
kiro-cli issue
kiro-cli issue "Brief description of the problem"
```

Desde el chat:
```
> /problema
```

### Información útil para soporte

Al reportar un problema, incluya:
- Salida de `kiro-cli diagnostic`
- Versión: `versión kiro-cli`
- Sistema operativo y shell
- Pasos para reproducir el problema
- Registros relevantes (`/logdump`)

---

## Códigos de salida comunes

| Código | causa |
|---|---|
| `0` | Éxito |
| `1` | Errores generales |
| `2` | Argumentos inválidos |
| `3` | Servidor(es) MCP no iniciaron |

Ver [Códigos de salida →](./17_Reference/04_Exit%20codes.md) para más detalles.