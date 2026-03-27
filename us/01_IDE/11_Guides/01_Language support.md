# Language Support

> **Source:** [kiro.dev/docs/guides/languages-and-frameworks/](https://kiro.dev/docs/guides/languages-and-frameworks/)

---

Kiro provee capacidades de desarrollo asistido por IA para los lenguajes más populares, ayudándote a escribir, debuguear y mantener código de forma más eficiente.

---

## TypeScript & JavaScript

> [kiro.dev/docs/guides/languages-and-frameworks/typescript-javascript-guide/](https://kiro.dev/docs/guides/languages-and-frameworks/typescript-javascript-guide/)

### Prerequisites
- [Node.js](https://nodejs.org/) — última versión
- [TypeScript](https://www.typescriptlang.org/) — global o local en el proyecto
- Package Manager: npm, yarn o pnpm
- [Git](https://git-scm.com/)

### Suggested Extensions

| Extensión | Propósito |
|---|---|
| [ESLint](https://open-vsx.org/extension/dbaeumer/vscode-eslint) | Linting en tiempo real |
| [Prettier](https://open-vsx.org/extension/esbenp/prettier-vscode) | Formateo automático |
| [Auto Rename Tag](https://open-vsx.org/extension/formulahendry/auto-rename-tag) | Renombrado automático de tags HTML/JSX |
| [ES6 Snippets](https://open-vsx.org/extension/xabikos/JavaScriptSnippets) | Snippets para JavaScript/TypeScript moderno |

### Steering

Kiro puede generar archivos de steering para tus proyectos TS/JS:

- `product.md` — Información del producto y sus características clave
- `tech.md` — Stack tecnológico y guidelines de desarrollo
- `structure.md` — Organización del proyecto

### Recommended Hooks

| Hook | Trigger | Acción |
|---|---|---|
| **Test generation** | File Save (`.ts/.tsx`) | `"Create a hook that generates Jest tests when I save a new component"` |
| **Type checking** | File Save | `"Set up a hook to run TypeScript type checking when I save files"` |
| **Dependency update** | File Save (`package.json`) | `"Create a hook that checks for outdated npm packages"` |
| **ESLint auto-fix** | File Save | Corre ESLint con `--fix` y reporta los issues restantes |
| **Component docs** | File Save (`.tsx`) | Extrae props, genera JSDoc y actualiza el README |

---

## Python

> [kiro.dev/docs/guides/languages-and-frameworks/python-guide/](https://kiro.dev/docs/guides/languages-and-frameworks/python-guide/)

### Prerequisites
- Python 3.8+ ([descargar](https://www.python.org/downloads/))
- pip (incluido con Python)
- Virtual environment: `venv`, `virtualenv` o `conda`
- Git

### Suggested Extensions

| Extensión | Propósito |
|---|---|
| [Python](https://open-vsx.org/extension/ms-python/python) | IntelliSense, debugging, linting, formateo |
| [PyLint](https://open-vsx.org/extension/ms-python/pylint) | Linting para archivos Python |
| [Jupyter](https://open-vsx.org/extension/ms-toolsai/jupyter) | Soporte para notebooks |
| [Python Debugger](https://open-vsx.org/extension/ms-python/debugpy) | Debugging con debugpy |
| [Rainbow CSV](https://open-vsx.org/extension/mechatroner/rainbow-csv) | Visualización de CSV/TSV |

### Steering Example: `python-conventions.md`

```markdown
# Python Conventions

## Naming Conventions
- snake_case para variables y funciones
- PascalCase para clases
- UPPER_SNAKE_CASE para constantes

## Code Style
- Seguir PEP 8
- Usar Black para formateo
- Máximo 88 caracteres por línea
- Type hints en todas las funciones públicas

## Documentation
- Docstrings para todas las funciones y clases públicas
- Estilo Google o NumPy
```

### Recommended Hooks

| Hook | Trigger | Prompt |
|---|---|---|
| **Test generation** | File Save (`.py`) | `"Create a hook that generates pytest tests when I save a new Python module"` |
| **Dependency update** | File Save (`requirements.txt`) | `"Create a hook that checks for outdated pip packages"` |
| **Linting** | File Save (`.py`) | Corre flake8/pylint, reporta issues, sugiere fixes, actualiza docstrings |
| **Virtual environment** | File Save (`requirements.txt` / `pyproject.toml`) | Verifica venv, instala deps, reporta conflictos |

---

## Java

> [kiro.dev/docs/guides/languages-and-frameworks/java-guide/](https://kiro.dev/docs/guides/languages-and-frameworks/java-guide/)

### Prerequisites
- JDK 17+ (se recomienda [Amazon Corretto](https://aws.amazon.com/corretto/))
- Build tool: Maven o Gradle
- Git

### Suggested Extensions

| Extensión | Propósito |
|---|---|
| [Extension Pack for Java](https://open-vsx.org/extension/vscjava/vscode-java-pack) | IntelliSense, Debug, Tests, Maven, Project Manager |
| [Spring Boot Extension Pack](https://open-vsx.org/extension/vmware/vscode-spring-boot) | Spring Boot Tools + Initializr + Dashboard |
| [Gradle for Java](https://open-vsx.org/extension/vscjava/vscode-gradle) | Gestión de proyectos Gradle |
| [Maven for Java](https://open-vsx.org/extension/vscjava/vscode-maven) | Gestión de proyectos Maven |

### Steering Examples

**`java-conventions.md`** — Patrones arquitectónicos y testing:
```markdown
# Java Project Conventions
## Architecture Patterns
- Hexagonal architecture para dominios complejos
- CQRS para separación lectura/escritura
## Testing Strategy
- Unit tests para toda la lógica de negocio
- TestContainers para tests de integración
- 80% code coverage mínimo
- Patrón AAA (Arrange, Act, Assert)
```

**`spring-boot-patterns.md`** — Guidelines para Spring Boot:
```markdown
# Spring Boot Development Guidelines
## Component Structure
- @RestController para endpoints REST
- @Service para lógica de negocio
- @Repository para acceso a datos
## Dependency Injection
- Constructor injection (no field injection)
- Usar fields final para dependencias inyectadas
```