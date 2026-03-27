# Soporte de idiomas

> **Fuente:** [kiro.dev/docs/guides/languages-and-frameworks/](https://kiro.dev/docs/guides/languages-and-frameworks/)

---

Kiro proporciona capacidades de desarrollo asistido por IA para los lenguajes más populares, ayudándote a escribir, debuguear y mantener código de forma más eficiente.

---

## Mecanografiado y JavaScript

> [kiro.dev/docs/guides/languages-and-frameworks/typescript-javascript-guide/](https://kiro.dev/docs/guides/languages-and-frameworks/typescript-javascript-guide/)

### Requisitos previos
- [Node.js](https://nodejs.org/) — última versión
- [TypeScript](https://www.typescriptlang.org/) — global o local en el proyecto
- Gestor de paquetes: npm, Yarn o pnpm
-[Git](https://git-scm.com/)

### Extensiones sugeridas

| Extensión | Propósito |
|---|---|
| [ESLint](https://open-vsx.org/extension/dbaeumer/vscode-eslint) | Linting en tiempo real |
| [Más bonita](https://open-vsx.org/extension/esbenp/prettier-vscode) | Formato automático |
| [Etiqueta de cambio de nombre automático](https://open-vsx.org/extension/formulahendry/auto-rename-tag) | Renombrado automático de etiquetas HTML/JSX |
| [Fragmentos de ES6](https://open-vsx.org/extension/xabikos/JavaScriptSnippets) | Fragmentos de JavaScript/TypeScript modernos |

### Steering

Kiro puede generar archivos de Steering para tus proyectos TS/JS:

- `product.md` — Información del producto y sus características clave
- `tech.md` — Stack tecnológico y pautas de desarrollo
- `structure.md` — Organización del proyecto

### Hooks recomendados

| Gancho | Gatillo | Acción |
|---|---|---|
| **Generación de prueba** | Guardar archivo (`.ts/.tsx`) | `"Crear un gancho que genere pruebas Jest cuando guardo un nuevo componente"` |
| **Comprobación de tipo** | Guardar archivo | `"Configurar un enlace para ejecutar la verificación de tipos de TypeScript cuando guardo archivos"` |
| **Actualización de dependencia** | Guardar archivo (`paquete.json`) | `"Crear un gancho que busque paquetes npm obsoletos"` |
| **Corrección automática de ESLint** | Guardar archivo | Corre ESLint con `--fix` y reporta los problemas restantes |
| **Documentos de los componentes** | Guardar archivo (`.tsx`) | Accesorios adicionales, genera JSDoc y actualiza el README |

---

## Pitón

> [kiro.dev/docs/guides/languages-and-frameworks/python-guide/](https://kiro.dev/docs/guides/languages-and-frameworks/python-guide/)

### Requisitos previos
- Python 3.8+ ([descargar](https://www.python.org/downloads/))
- pip (incluido con Python)
- Entorno virtual: `venv`, `virtualenv` o `conda`
-Git

### Extensiones sugeridas

| Extensión | Propósito |
|---|---|
| [Python](https://open-vsx.org/extension/ms-python/python) | IntelliSense, depuración, linting, formateo |
| [PyLint](https://open-vsx.org/extension/ms-python/pylint) | Linting para archivos Python |
| [Jupyter](https://open-vsx.org/extension/ms-toolsai/jupyter) | Soporte para portátiles |
| [Depurador de Python](https://open-vsx.org/extension/ms-python/debugpy) | Depuración con debugpy |
| [Arcoíris CSV](https://open-vsx.org/extension/mechatroner/rainbow-csv) | Visualización de CSV/TSV |

### Ejemplo de dirección: `python-conventions.md`

```markdown
# Convenciones de Python

## Convenciones de nomenclatura
- Snake_case para variables y funciones.
- PascalCase para clases
- UPPER_SNAKE_CASE para constantes

## Estilo de código
- Seguir PEP 8
- Usar Black para formatear
- Máximo 88 caracteres por línea
- Escribe sugerencias en todas las funciones públicas.

## Documentación
- Docstrings para todas las funciones y clases públicas
- Estilo Google o NumPy
```

### Hooks recomendados

| Gancho | Gatillo | Aviso |
|---|---|---|
| **Generación de prueba** | Guardar archivo (`.py`) | `"Crear un gancho que genere pruebas de pytest cuando guardo un nuevo módulo de Python"` |
| **Actualización de dependencia** | Guardar archivo (`requisitos.txt`) | `"Crear un gancho que busque paquetes de pip obsoletos"` |
| **pelusa** | Guardar archivo (`.py`) | Corre flake8/pylint, informa problemas, sugiere correcciones, actualiza cadenas de documentos |
| **Entorno virtual** | Guardar archivo (`requirements.txt` / `pyproject.toml`) | Verifica venv, instala deps, reporta conflictos |

---

##Java

> [kiro.dev/docs/guides/languages-and-frameworks/java-guide/](https://kiro.dev/docs/guides/languages-and-frameworks/java-guide/)

### Requisitos previos
- JDK 17+ (se recomienda [Amazon Corretto](https://aws.amazon.com/corretto/))
- Herramienta de construcción: Maven o Gradle
-Git

### Extensiones sugeridas

| Extensión | Propósito |
|---|---|
| [Paquete de extensión para Java](https://open-vsx.org/extension/vscjava/vscode-java-pack) | IntelliSense, Depuración, Pruebas, Maven, Gerente de Proyecto |
| [Paquete de extensión Spring Boot](https://open-vsx.org/extension/vmware/vscode-spring-boot) | Herramientas de arranque de primavera + Inicializr + Panel de control |
| [Gradle para Java](https://open-vsx.org/extension/vscjava/vscode-gradle) | Gestión de proyectos Gradle |
| [Maven para Java](https://open-vsx.org/extension/vscjava/vscode-maven) | Gestión de proyectos Maven |

### Ejemplos de dirección

**`java-conventions.md`** — Patrones arquitectónicos y pruebas:
```markdown
# Convenciones del proyecto Java
## Patrones de arquitectura
- Arquitectura hexagonal para dominios complejos
- CQRS para separación lectura/escritura
## Estrategia de prueba
- Pruebas unitarias para toda la lógica de negocio.
- TestContainers para pruebas de integración
- 80% de cobertura de código mínimo
- Patrón AAA (Ordenar, Actuar, Afirmar)
```

**`spring-boot-patterns.md`** — Directrices para Spring Boot:
```markdown
# Pautas de desarrollo de Spring Boot
## Estructura de componentes
- @RestController para puntos finales REST
- @Service para lógica de negocio
- @Repository para acceder a datos
## Inyección de dependencia
- Inyección de constructor (sin inyección de campo)
- Usar campos finales para dependencias inyectadas
```