# Listas de tareas pendientes

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#todo-lists)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

## Descripción general

TODO Lists permite a Kiro crear y modificar listas de tareas automáticamente durante las sesiones de chat, con comandos para verlas y gestionarlas.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableTodoList verdadero
```

**Comando:** `/todo`

---

## Características

- Kiro crea automáticamente TODOs cuando es apropiado
- Ver, gestionar y eliminar TODOs
- Retomar listas de TODO existentes
- Persistidas entre sesiones de chat.

---

## Uso

```
# Kiro crea TODOs automáticamente al planear tareas complejas
> Implementar la autenticación de usuarios con JWT

#manual de gestión
/todo list # Ver todos los TODOs
/todo show <id> # Ver detalles de un TODO
/todo eliminar <id> # Eliminar un TODO
/todo resume <id> # Retomar un TODO existente
```

---

## Flujo de ejemplo

```
> Implementar una API REST con autenticación de usuario, catálogo de productos y gestión de pedidos

Kiro crea automáticamente:
☐ 1. Configurar la estructura y las dependencias del proyecto.
☐ 2. Implementar la autenticación de usuario (JWT)
☐ 3. Crear puntos finales del catálogo de productos
☐ 4. Construir un sistema de gestión de pedidos
☐ 5. Agregar pruebas unitarias

> /lista de tareas pendientes
[TODO 1234] "Implementación de API REST" - 0/5 completo
```

---

## Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos completos de listas de TODO →](https://kiro.dev/docs/cli/experimental/todo-lists)