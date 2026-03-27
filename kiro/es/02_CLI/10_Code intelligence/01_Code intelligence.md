# Inteligencia de código

> **Fuente:** [kiro.dev/docs/cli/code-intelligence/](https://kiro.dev/docs/cli/code-intelligence/)

---

Code Intelligence proporciona una comprensión profunda del código mediante el uso de Tree-sitter (integrado) y la integración LSP opcional para la búsqueda de símbolos, la coincidencia de patrones y la exploración de la base de código, todo sin salir de su terminal.

---

## Idiomas admitidos

Bash, C, C++, C#, Elixir, Go, Java, JavaScript, Kotlin, Lua, PHP, Python, Ruby, Rust, Scala, Swift, TSX, TypeScript

---

## Funciones integradas *(no se requiere LSP)*

| Característica | Descripción |
|---|---|
| **Búsqueda de símbolos** | Buscar funciones, clases y métodos por nombre (coincidencia difusa) |
| **Símbolos del documento** | Listar todos los símbolos en un archivo |
| **Búsqueda de símbolos** | Busque símbolos específicos por nombre exacto |
| **Búsqueda de patrones** | Búsqueda de códigos estructurales basada en AST |
| **Reescritura de patrón** | Transformaciones de código automatizadas utilizando patrones AST |
| **Descripción general del código base** | Descripción general de la estructura base del código de alto nivel |
| **Mapa de código base** | Explorar la estructura del directorio y la organización del código |

---

## Descripción general de la base de código

Obtenga una descripción completa de cualquier Workspace en segundos:

```bash
/code overview
```

Centrarse en un directorio específico:
```golpecito
/descripción general del código ./src/components
```

Utilizá `--silent` para obtener resultados más limpios cuando profundice en un paquete:
```golpecito
/ descripción general del código --silencioso
```

Ideal para: incorporación a nuevas bases de código, preguntas y respuestas sobre la estructura del proyecto y comprensión rápida de paquetes desconocidos.

---

## Generación de documentación

Genere documentación para su código base con una sesión interactiva:

```bash
/code summary
```

Elija el formato de salida:
- **AGENTS.md** — Documentación para agentes de IA que trabajan con su código base
- **README.md** — Documentación estándar del proyecto
- **CONTRIBUTING.md** — Directrices para contribuyentes

---

## Búsqueda y reescritura de patrones

Búsqueda y transformación de código estructural basada en AST. Busque y modifique código por estructura, no solo por texto.

### Metavariables

Utilizá metavariables (por ejemplo, `$FUNC`, `$ARG`) en patrones para que coincidan con cualquier expresión de ese tipo.

### Ejemplos de búsqueda de patrones

```bash
# Find all function calls with specific patterns
/code search "console.log($MSG)"
```

### Ejemplos de reescritura de patrones

```bash
# Replace deprecated API calls
/code rewrite "oldAPI($ARG)" --to "newAPI($ARG)"
```

---

## Integración LSP *(Opcional)*

Las funciones integradas de cuidado de árboles funcionan desde el primer momento. Ejecute `/code init` solo si desea funciones LSP mejoradas.

> La inteligencia del código se configura por Workspace: cada proyecto mantiene su propia configuración de LSP de forma independiente.

```bash
/code init
```

**Operaciones adicionales impulsadas por LSP:**

| Característica | Descripción |
|---|---|
| **Buscar referencias** | Localice todos los usos de un símbolo en una posición |
| **Ir a la definición** | Navegue hasta donde se define un símbolo |
| **Cambiar nombre del símbolo** | Cambiar el nombre de los símbolos en todo el código base |
| **Obtener diagnóstico** | Obtener errores y advertencias para un archivo |
| **Documentación al pasar el mouse** | Obtenga información y documentación sobre el tipo en la posición |
| **Finalizaciones** | Obtenga sugerencias de finalización en la posición |

---

## Comandos de barra diagonal

| Comando | Descripción |
|---|---|
| `/ código de inicio` | Inicializar LSP para el Workspace actual |
| `/ código de inicio -f` | Forzar reinicializar LSP |
| `/estado del código` | Mostrar el estado actual de la conexión LSP |
| `/ registros de código` | Ver registros de diagnóstico de LSP |