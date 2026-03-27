# Hook Examples

> **Source:** [kiro.dev/docs/hooks/examples/](https://kiro.dev/docs/hooks/examples/)

---

Ejemplos prácticos y templates listos para usar en tus proyectos.

---

## Security Pre-Commit Scanner

Previene leaks de seguridad escaneando archivos antes de ser commiteados.

| Campo | Valor |
|---|---|
| **Trigger** | Agent Stop |
| **Action** | Agent Prompt |

**Prompt:**
```
Review changed files for potential security issues:
1. Look for API keys, tokens, or credentials in source code
2. Check for private keys or sensitive credentials
3. Scan for encryption keys or certificates
4. Identify authentication tokens or session IDs
5. Flag passwords or secrets in configuration files
6. Detect IP addresses containing sensitive data
7. Find hardcoded internal URLs
8. Spot database connection credentials

For each issue found:
1. Highlight the specific security risk
2. Suggest a secure alternative approach
3. Recommend security best practices
```

---

## Centralized User Prompt Logging

Loguea todos los prompts de usuario a un sistema centralizado para análisis y auditoría.

| Campo | Valor |
|---|---|
| **Trigger** | Prompt Submit |
| **Action** | Shell Command |

**Command:**
```bash
# Log user prompt to Grafana Loki
curl -H "Content-Type: application/json" -XPOST \
  "http://loghost/loki/api/v1/push" --data-raw \
  "{'streams': [{ 'stream': { 'app': 'kiro', 'user': \"${USER}\" }, 'values': [ [\"$(date +%s%N)\", \"${USER_PROMPT}\"] ] }]}"
```

---

## Internationalization Helper

Mantiene las traducciones sincronizadas cuando se actualiza el archivo del idioma principal.

| Campo | Valor |
|---|---|
| **Trigger** | File Save |
| **Target** | `src/locales/en/*.json` |
| **Action** | Agent Prompt |

**Prompt:**
```
When an English locale file is updated:
1. Identify which string keys were added or modified
2. Check all other language files for these keys
3. For missing keys, add them with a "NEEDS_TRANSLATION" marker
4. For modified keys, mark them as "NEEDS_REVIEW"
5. Generate a summary of changes needed across all languages
```

---

## Test Coverage Maintainer

Asegura que la cobertura de tests se mantenga alta a medida que el código evoluciona.

| Campo | Valor |
|---|---|
| **Trigger** | File Save |
| **Target** | `src/**/*.{js,ts,jsx,tsx}` |
| **Action** | Agent Prompt |

**Prompt:**
```
When a source file is modified:
1. Identify new or modified functions and methods
2. Check if corresponding tests exist and cover the changes
3. If coverage is missing, generate test cases for the new code
4. Run the tests to verify they pass
5. Update coverage reports
```

---

## Documentation Generator

Genera documentación completa bajo demanda para el archivo actual.

| Campo | Valor |
|---|---|
| **Trigger** | Manual |
| **Action** | Agent Prompt |

**Prompt:**
```
Generate comprehensive documentation for the current file:
1. Extract function and class signatures
2. Document parameters and return types
3. Provide usage examples based on existing code
4. Update the README.md with any new exports
5. Ensure documentation follows project standards
```

---

## Integration with MCP

Los hooks pueden potenciarse con MCP para acceder a herramientas externas especializadas.

**Cómo usar MCP con hooks:**
1. [Configurar MCP servers →](../13_MCP/01_Configuration.md)
2. Referenciar los MCP tools en las instrucciones del hook
3. Configurar `autoApprove` para tools de uso frecuente

**Casos de uso:**
- Verificar que tu sistema de diseño Figma sea respetado
- Actualizar el estado de un ticket después de completar una tarea
- Sincronizar una base de datos desde archivos del proyecto