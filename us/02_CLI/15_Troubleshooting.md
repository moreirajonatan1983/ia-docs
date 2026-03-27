# Troubleshooting — Kiro CLI

> **Source:** [kiro.dev/docs/cli/troubleshooting/](https://kiro.dev/docs/cli/troubleshooting/) | [kiro.dev/docs/cli/reference/cli-commands/](https://kiro.dev/docs/cli/reference/cli-commands/)

---

## Diagnostic Tools

### Diagnóstico automático

```bash
kiro-cli doctor          # Diagnóstico estándar
kiro-cli doctor --all    # Todos los checks disponibles
kiro-cli doctor --strict # Modo estricto (falla en warnings)
```

### Reporte completo del sistema

```bash
kiro-cli diagnostic
kiro-cli diagnostic --format json-pretty   # Output estructurado
kiro-cli diagnostic --force                # Sin requerir que la app esté corriendo
```

### Logs de debug

```bash
kiro-cli --verbose chat "..."    # -v / -vv / -vvv para más detalle
kiro-cli diagnostic              # Ver versión, OS, env vars, paths
```

### Log dump para soporte

Desde el chat:
```
> /logdump          # Chat logs
> /logdump --mcp    # Chat + MCP server logs
```
Crea un archivo `q-logs-YYYY-MM-DDTHH-MM-SSZ.zip` en el directorio actual.

---

## Authentication Issues

### "Already logged in" error

```bash
kiro-cli logout
kiro-cli login
```

### Browser doesn't open (SSH/Remote)

```bash
kiro-cli login --use-device-flow
```
Muestra un device code y URL para autenticar desde otro dispositivo.

### Identity Center authentication fails

Verificá con tu administrador:
- URL correcta del Identity Center
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

## Installation Issues

### `kiro-cli` command not found

```bash
which kiro-cli
# Verificar que el path esté en $PATH

# Agregar al .zshrc / .bashrc:
export PATH="$HOME/.local/bin:$PATH"
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

## Chat / Connectivity Issues

### Network / Proxy

```bash
export HTTPS_PROXY=http://proxy.company.com:8080
export NO_PROXY=localhost,127.0.0.1

# Verificar conectividad
curl -v https://api.kiro.dev/health
```

### API Timeout

```bash
kiro-cli settings api.timeout 60    # Aumentar a 60s (default: 30s)
```

### Context window lleno

Kiro compacta automáticamente el contexto. Para hacerlo manual:
```
> /compact
```

---

## MCP Server Issues

### MCP server no inicia

```bash
# Ver estado de servidores MCP
kiro-cli mcp list
kiro-cli mcp status --name my-server

# Verificar en el chat
> /mcp

# Forzar fallo si MCP es crítico
kiro-cli chat --require-mcp-startup ...
```

### Logs de MCP servers

```
> /logdump --mcp
```

### Timeout de inicialización

```bash
kiro-cli settings mcp.initTimeout 30    # Aumentar timeout (default: 10s)
```

---

## Custom Agent Issues

### Agent no se carga

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

Ver [Custom Agents Troubleshooting →](./04_Custom%20agents/04_Troubleshooting.md) para errores específicos.

---

## Code Intelligence Issues

### LSP no responde

```bash
> /code init -f    # Forzar reinicialización
> /code status     # Ver estado del servidor LSP
> /code logs       # Ver logs de LSP
```

---

## Autocomplete Issues

### Autocompletado no funciona

```bash
kiro-cli doctor    # Verificar instalación
# Reiniciar terminal después de instalación
# Verificar integración en .bashrc / .zshrc
```

### Sugerencias inline deshabilitadas

```bash
kiro-cli inline enable
kiro-cli inline status
```

---

## Reporting Issues

### Crear un issue de soporte

```bash
kiro-cli issue
kiro-cli issue "Brief description of the problem"
```

Desde el chat:
```
> /issue
```

### Información útil para soporte

Al reportar un problema, incluir:
- Output de `kiro-cli diagnostic`
- Versión: `kiro-cli version`
- Sistema operativo y shell
- Pasos para reproducir el problema
- Logs relevantes (`/logdump`)

---

## Common Exit Codes

| Código | Causa |
|---|---|
| `0` | Éxito |
| `1` | Error general |
| `2` | Argumentos inválidos |
| `3` | MCP server(s) no iniciaron |

Ver [Exit Codes →](./17_Reference/04_Exit%20codes.md) para más detalles.