# Tangent Mode

> **Source:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#tangent-mode)

> ⚠️ **Feature experimental** — puede cambiar en futuras versiones.

---

## Overview

Tangent Mode permite crear **checkpoints de conversación** para explorar temas secundarios sin interrumpir el flujo principal de la conversación.

**Habilitar:**
```bash
kiro-cli settings chat.enableTangentMode true
```

**Activar:** `/tangent` o `Ctrl+T`

---

## Features

- Crear checkpoints de conversación
- Explorar temas tangenciales
- Volver al hilo principal de conversación
- Preservar el contexto de la conversación

---

## How It Works

```
> Estoy implementando autenticación con JWT...
> /tangent    # o Ctrl+T — crea un checkpoint aquí

[tangent] > ¿Cuál es la diferencia entre RS256 y HS256?
[tangent] > ¿Cuándo usar cada uno?

> /tangent    # vuelve al checkpoint anterior

> Continuando con JWT... (contexto preservado)
```

---

## Use Cases

- Hacer preguntas de contexto sin perder el hilo principal
- Explorar alternativas antes de comprometerse con un enfoque
- Investigar un error sin contaminar la conversación principal
- Aprender sobre una tecnología mientras trabajás en otra tarea

---

## Learn More

- [Experimental features overview →](https://kiro.dev/docs/cli/experimental/)
- [Full Tangent Mode docs →](https://kiro.dev/docs/cli/experimental/tangent-mode)