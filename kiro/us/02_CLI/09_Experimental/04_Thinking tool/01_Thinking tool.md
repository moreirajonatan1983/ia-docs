# Thinking Tool

> **Source:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#thinking-tool)

> ⚠️ **Feature experimental** — puede cambiar en futuras versiones.

---

## Overview

El Thinking Tool muestra el **proceso de razonamiento de la IA** para problemas complejos, con procesos de pensamiento paso a paso visibles para el usuario.

**Habilitar:**
```bash
kiro-cli settings chat.enableThinking true
```

---

## Features

- Proceso de toma de decisiones transparente
- Visualización del razonamiento paso a paso
- Útil para debugging y aprendizaje
- Mejor comprensión de las conclusiones del agente

---

## Example Output

```
> Why is my API returning 401 even with a valid token?

[thinking]
1. The user has a valid token but gets 401
2. Possible causes:
   - Token format incorrect (Bearer prefix missing)
   - Token expired
   - Wrong signing algorithm
   - Header name mismatch
3. Need to check: middleware configuration, token validation logic
[/thinking]

Looking at your code, the issue is likely in the middleware...
```

---

## Use Cases

- **Debugging complejo** — Ver cómo el agente analiza el problema
- **Aprendizaje** — Entender el razonamiento detrás de las decisiones
- **Validación** — Verificar que el agente está considerando los factores correctos
- **Arquitectura** — Evaluar trade-offs en decisiones de diseño

---

## Learn More

- [Experimental features overview →](https://kiro.dev/docs/cli/experimental/)
- [Full Thinking Tool docs →](https://kiro.dev/docs/cli/experimental/thinking)