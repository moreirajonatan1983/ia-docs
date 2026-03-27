# Gestión del contexto

> **Fuente:** [kiro.dev/docs/cli/chat/context/](https://kiro.dev/docs/cli/chat/context/)

---

## Elegir el enfoque contextual adecuado

| Escenario | Enfoque |
|---|---|
| Archivos de proyecto esenciales (README, configuraciones, estándares) | **Recursos para agentes** |
| Grandes bases de código o conjuntos de documentación | **Bases de conocimiento** |
| Archivos temporales para la tarea actual | **Contexto de la sesión** |

---

## Gestión del contexto

### Contexto persistente a través de recursos del agente

La forma recomendada de configurar el contexto es a través del campo "recursos" en la configuración de su agente. Esto crea un contexto persistente disponible en cada sesión.

```json
{
  "name": "my-agent",
  "description": "My development agent",
  "resources": [
    "file://README.md",
    "file://docs/**/*.md",
    "file://src/config.py"
  ]
}
```

**Esquemas de URI de recursos:**
- `file://` — Archivos cargados directamente en contexto al inicio
- `skill://` — Habilidades con metadatos cargados al inicio, contenido completo bajo demanda
- `knowledgeBase` — Contenido indexado buscado bajo demanda (configurado como objetos)

### Contexto de sesión temporal

Agregue archivos a la sesión actual solo con `/context add`:

```
> / contexto agregar README.md
Se agregaron 1 ruta(s) al contexto.

> /contexto agregar documentos/*.md
Se agregaron 3 rutas al contexto.
```

⚠️ El contexto de la sesión **no es persistente**: no está disponible en sesiones nuevas.

### Bases de conocimientos (para grandes conjuntos de datos)

Para bases de código grandes o documentación que excedería los límites de la ventana de contexto:

```bash
kiro-cli settings chat.enableKnowledge true
```

```
> /knowledge add /path/to/large-codebase --include "/*.py" --exclude "node_modules/"
```

Las bases de conocimiento se buscan bajo demanda cuando es relevante, ideal para materiales de referencia de gran tamaño.

### Compactación de conversaciones

La compactación resume los mensajes más antiguos para liberar espacio en la ventana contextual.

- **Manual:** `/compacto`
- **Automático:** Se activa cuando la ventana de contexto se desborda

Después de la compactación, se crea una nueva sesión. Reanudar el original a través de `/chat resume`.

### Visualización del uso del contexto

```
> /context show
Current context window (5.9% used)
  Context files    0.9%
  Tools            0.5%
  Kiro responses   0.7%
  Your prompts     3.8%
```

---

## Eliminando contexto

Utilice `/context remove <ruta>` para eliminar archivos específicos del contexto de la sesión actual.

---

## Mejores prácticas

- **Organización de archivos de contexto**: archivos relacionados con el grupo; usar patrones globales para directorios
- **Rendimiento**: evite cargar archivos binarios o generados automáticamente de gran tamaño (node_modules, dist, build)
- **Seguridad**: nunca agregue archivos que contengan secretos o credenciales a los recursos del agente