# Control de fuente

> **Fuente:** [kiro.dev/docs/editor/source-control/](https://kiro.dev/docs/editor/source-control/)

---

Kiro mejora su flujo de trabajo de Git con la generación de mensajes de commit impulsada por IA y una perfecta integración del control de versiones.

---

## Confirmar generación de mensajes

![Mensaje de commit de Git](https://kiro.dev/videos/git-commit-message.mp4)

Kiro puede generar automáticamente mensajes de commit descriptivos siguiendo el formato [Commits convencionales](https://www.conventionalcommits.org/en/v1.0.0/) analizando sus cambios por etapas.

### Cómo generar mensajes de commit

1. **Prepara tus cambios** en el panel de control de código fuente
2. Haga clic en el botón **🪄** junto al campo de entrada del mensaje de commit.
3. **Revise el mensaje generado**: Kiro analiza sus cambios y crea un mensaje de commit descriptivo.
4. **Edite si es necesario**: puede modificar el mensaje generado antes de confirmarlo.
5. **Confirma tus cambios** usando el mensaje generado o editado

> **Consejo:** Puedes configurar un atajo de teclado personalizado para `Kiro: Generar mensaje de commit` en la configuración de tu teclado para un acceso más rápido.

---

### Formato del mensaje

Kiro sigue el formato de **Compromisos Convencionales**:

```
<type>(<scope>): <subject>
- First change or addition
- Second change or improvement
- Third change if applicable
- Why this change was needed (if relevant)
```

### Tipos de compromiso convencionales

| Tipo | Descripción |
|---|---|
| `hazaña` | Nuevas características |
| `arreglar` | Corrección de errores |
| `docs` | Cambios en la documentación |
| `estilo` | Cambios de formato |
| `refactor` | Reestructuración del código |
| `prueba` | Agregar/actualizar pruebas |
| `tarea` | Tareas de mantenimiento |
| `perfeccionamiento` | Mejoras de rendimiento |
| `ci` | Cambios CI/CD |

### Ejemplo

```
feat(docs): add comprehensive Source Control documentation
- Create new documentation page for Source Control features
- Update interface documentation to link to Source Control page
- Provide detailed explanation of AI-powered commit message generation
- Describe diff context provider and commit message generation process
```

---

## Proveedor de contexto Git Diff

Kiro incluye un proveedor de contexto `#Git Diff` que le permite hacer referencia a sus cambios actuales no confirmados directamente en el chat. Esto es útil para:

- Solucionar conflictos de fusión
- Revisar los cambios antes de comprometerlos.
- Obtener una revisión del código de tu diferencia actual

### Ejemplo de uso

```
Hey Kiro, can you fix the merge conflicts? #Git Diff
```

---

## Solución de problemas

### Error en las operaciones de Git

- Verifique su configuración y credenciales de Git
- Asegúrese de tener los permisos adecuados para el repositorio.