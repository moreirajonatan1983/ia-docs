# TODO Lists

> **Source:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#todo-lists)

> ⚠️ **Feature experimental** — puede cambiar en futuras versiones.

---

## Overview

TODO Lists permite a Kiro crear y modificar listas de tareas automáticamente durante las sesiones de chat, con comandos para verlas y gestionarlas.

**Habilitar:**
```bash
kiro-cli settings chat.enableTodoList true
```

**Comando:** `/todo`

---

## Features

- Kiro crea automáticamente TODOs cuando es apropiado
- Ver, gestionar y eliminar TODOs
- Retomar listas de TODOs existentes
- Persistidas entre sesiones de chat

---

## Usage

```
# Kiro crea TODOs automáticamente al planear tareas complejas
> Implement user authentication with JWT

# Gestión manual
/todo list           # Ver todos los TODOs
/todo show <id>      # Ver detalles de un TODO
/todo delete <id>    # Eliminar un TODO
/todo resume <id>    # Retomar un TODO existente
```

---

## Example Flow

```
> Implement a REST API with user auth, product catalog, and order management

Kiro crea automáticamente:
☐ 1. Set up project structure and dependencies
☐ 2. Implement user authentication (JWT)
☐ 3. Create product catalog endpoints
☐ 4. Build order management system
☐ 5. Add unit tests

> /todo list
[TODO 1234] "REST API Implementation" - 0/5 complete
```

---

## Learn More

- [Experimental features overview →](https://kiro.dev/docs/cli/experimental/)
- [Full TODO Lists docs →](https://kiro.dev/docs/cli/experimental/todo-lists)