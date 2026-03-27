# Charlar

> **Fuente:** [kiro.dev/docs/chat/](https://kiro.dev/docs/chat/)

---

La interfaz de chat de Kiro es la forma principal de interactuar con el agente de IA para conversaciones contextuales, asistencia para el desarrollo y generación de código.

---

## Empezando

### Accediendo al chat

| Método | Atajo |
|---|---|
| Atajo de teclado | `Cmd+L` (Mac) / `Ctrl+L` (Windows/Linux) |
| Paleta de comandos | `Cmd+Shift+P` → buscar "Kiro: Abrir Chat" |
| Barra lateral secundaria | `Cmd+Opción+B` (Mac) / `Ctrl+Alt+B` (Windows/Linux) |

### Soporte multilingüe

Kiro chat admite múltiples idiomas naturales, incluidos: mandarín, francés, alemán, italiano, japonés, español, coreano, hindi, portugués y más. Kiro detecta automáticamente tu idioma y responde en el mismo idioma.

### Tu primera conversación

1. Escriba su pregunta o solicitud en lenguaje natural en la entrada del chat.
2. Presione **Entrar** para enviar
3. Kiro analizará tu solicitud y responderá adecuadamente

**Solicitudes de ejemplo:**
```
"Explica cómo funciona la autenticación en este proyecto"
"Crear un componente React para una página de perfil de usuario"
"Ayúdame a corregir el error en esta función"
```

### Exportar una conversación

Haga clic derecho en la pestaña de la conversación → **Exportar conversación** → guarda como formato `.md`.

### Detección inteligente de intenciones

Kiro detecta inteligentemente tu intención:
- **Solicitudes de información** ("¿Cómo funciona esto?", "¿Cuál es el propósito de este código?") → Responde con explicaciones sin modificar el código.
- **Solicitudes de acción** ("Crear un componente", "Corregir este error") → Propone o implementa cambios de código

---

## Gestión del contexto

### Proveedores de contexto

Utilice el símbolo `#` en la entrada del chat para acceder a los proveedores de contexto:

| Proveedor | Uso de ejemplo |
|---|---|
| `#base de código` | `#codebase explica el flujo de autenticación` |
| `#archivo` | `#auth.ts explica esta implementación` |
| `#carpeta` | `#componentes/ ¿qué componentes tenemos?` |
| `#git diff` | `#git diff explica qué cambió en este PR` |
| `#terminal` | `#terminal ayúdame a corregir este error de compilación` |
| `#problemas` | `#problemas me ayudan a resolver estos problemas` |
| `#url` | `#url:https://docs.example.com/api explica esta API` |
| `#código` | `#código: suma constante = (a, b) => a + b; explica esta función` |
| `#repositorio` | `#repositorio ¿cómo está organizado este proyecto?` |
| `#actual` | `#actual explica este componente` |
| `#dirección` | `#steering:coding-standards.md revisa mi código` |
| `#docs` | `#docs:api-reference.md explica este punto final de API` |
| `#especificación` | `#spec: la autenticación de usuario actualiza el archivo de diseño` |
| `#mcp` | `#mcp:aws-docs ¿Cómo configuro los depósitos S3?` |

Combine múltiples proveedores de contexto:
```
#codebase #auth.ts explica cómo funciona la autenticación con nuestra base de datos
```

El proveedor de contexto `#terminal` es particularmente poderoso para la depuración:
```
#terminal Mi compilación está fallando, ¿cuál es el problema?
#terminal Estas pruebas no pasan, ayúdame a entender por qué
#terminal npm install arroja errores
```

---

## Sesiones e Historia

### Gestión de sesiones

- **Nueva sesión:** Haga clic en el ícono **+** en el panel de chat.
- **Cambiar de sesión:** Navega usando el selector de pestañas
- **Ver historial:** Haga clic en el botón **Historial**
- **Seguimiento de tareas:** Supervise el progreso mediante el botón **Lista de tareas**

### Historial de ejecución

Kiro mantiene un historial detallado de las sesiones que incluye: cambios de código, comandos ejecutados, resultados de búsqueda y operaciones de archivos. Puede **buscar**, **restaurar** o **eliminar** sesiones específicas.