# Steering

> **Fuente:** [kiro.dev/docs/steering/](https://kiro.dev/docs/steering/)

---

Los archivos de Steering guían la IA de Kiro con un contexto global o específico del Workspace a través de documentos Markdown que definen sus estándares, arquitectura y convenciones, lo que le brinda a Kiro una comprensión persistente de cómo funciona su proyecto.

---

## ¿Qué es el Steering?

Los archivos de Steering son documentos Markdown almacenados en `.kiro/steering/` que Kiro lee automáticamente durante las interacciones de chat. Proporcionan conocimiento específico del proyecto que da forma a las sugerencias, la generación de código y el comportamiento de Kiro.

**Beneficios clave:**
- Mantener una calidad de código consistente en todas las sesiones.
- Compartir convenciones de equipo automáticamente
- Reducir las correcciones repetitivas
- Habilitar experiencia en un dominio específico

---

## Alcance del archivo de Steering

### Steering del Workspace

Reside en `.kiro/steering/` en la raíz de tu Workspace. Aplicar solo a ese Workspace específico. Se utiliza para informar a Kiro sobre patrones, bibliotecas y estándares que se aplican a un Workspace individual.

### Steering global

Reside en `~/.kiro/steering/` en tu directorio de inicio. Aplicar a **todos** los Workspaces. Se utiliza para informar a Kiro sobre las convenciones que se aplican en todos sus proyectos.

> **Nota:** En caso de instrucciones contradictorias entre el Steering global y del Workspace, **el Steering del Workspace tiene prioridad**.

### Steering del equipo

El Steering global puede distribuir archivos de Steering centralizados a equipos completos a través de soluciones MDM, políticas de grupo o descargándolos desde un repositorio central a `~/.kiro/steering`.

---

## Archivos de Steering fundamentales

Hacé clic en **Generar documentos de Steering** en el panel de Kiro para generar automáticamente tres archivos fundamentales:

- **Descripción del producto** (`product.md`) — Define el propósito de tu producto, los usuarios objetivo, las funcionalidades clave y los objetivos de negocio.
- **Stack tecnológico** (`tech.md`) — Documenta tu elección de frameworks, librerías, herramientas de desarrollo y limitaciones técnicas.
- **Estructura del proyecto** (`structure.md`) — Describe la organización de archivos, convenciones de nombres, patrones de importación y decisiones arquitectónicas.
| `api-estándares.md` | Convenciones REST, formatos de respuesta de error, flujos de autenticación, estrategias de control de versiones |
| `testing-standards.md` | Patrones de pruebas unitarias, estrategias de integración, mocks, expectativas de cobertura |
| `código-convenciones.md` | Patrones de nombres, organización de archivos, ordenamiento de importaciones, decisiones arquitectónicas |
| `políticas-de-seguridad.md` | Requisitos de autenticación, validación de datos, desinfección de entradas, prevención de vulnerabilidades |
| `despliegue-flujo de trabajo.md` | Procedimientos de compilación, configuraciones del entorno, detalles de la canalización de CI/CD |