# Dirección - Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/steering/](https://kiro.dev/docs/cli/steering/)

---

Los archivos de dirección guían la IA de Kiro con el contexto específico del proyecto a través de documentos de rebajas que definen sus estándares, arquitectura y convenciones.

---

## ¿Qué es la dirección?

Los archivos de dirección son documentos de rebajas almacenados en `.kiro/steering/` que Kiro lee automáticamente durante las sesiones de chat. Proporcionan conocimiento específico del proyecto que da forma a la generación y el comportamiento del código de Kiro.

**Beneficios clave:**
- Calidad de código consistente en todas las sesiones.
- Aplicación automática de convenciones de equipo.
- Correcciones repetitivas reducidas
- Experiencia en un dominio específico

---

## Alcance del archivo directivo

### Dirección del espacio de trabajo

Reside en `.kiro/steering/` en la raíz de tu espacio de trabajo. Aplicar solo a ese espacio de trabajo específico.

### Dirección global

Reside en `~/.kiro/steering/` en tu directorio de inicio. Aplicar a **todos** los espacios de trabajo.

> **Nota:** En caso de instrucciones contradictorias, **la dirección del espacio de trabajo tiene prioridad** sobre la dirección global.

### Dirección del equipo

Los archivos de dirección globales se pueden distribuir a equipos completos a través de soluciones MDM, políticas de grupo o descargar desde un repositorio central a `~/.kiro/steering`.

---

## Archivos directivos fundamentales

Cree archivos de dirección fundamentales en `.kiro/steering/` (espacio de trabajo) o `~/.kiro/steering` (global):

| Archivo | Propósito |
|---|---|
| `producto.md` | Propósito del producto, usuarios objetivo, características clave y objetivos comerciales |
| `tecnología.md` | Marcos, bibliotecas, herramientas de desarrollo y limitaciones técnicas |
| `estructura.md` | Organización de archivos, convenciones de nomenclatura, patrones de importación y decisiones arquitectónicas |

Estos archivos básicos se incluyen en cada interacción de forma predeterminada.

---

## Creación de archivos de dirección personalizados

1. Cree un nuevo archivo `.md` en `.kiro/steering/`
2. Elija un nombre de archivo descriptivo (por ejemplo, `api-standards.md`)
3. Escriba su guía utilizando rebajas estándar y lenguaje natural.

---

## Dirección con agentes personalizados

Cuando se utilizan [agentes personalizados](https://kiro.dev/docs/cli/custom-agents/creating), los archivos de dirección **no se incluyen automáticamente**. Agréguelos explícitamente a la configuración de "recursos" del agente:

```json
{
  "resources": ["file://.kiro/steering/**/*.md"]
}
```

Este patrón global garantiza que todos los archivos de rebajas en su directorio de dirección se carguen cuando se utiliza el agente.

---

## Agentes.md

Kiro admite el estándar [AGENTS.md](https://agents.md/). Agregue archivos `AGENTS.md` a `~/.kiro/steering/` o a la carpeta raíz de su espacio de trabajo; **siempre se incluyen** automáticamente.

---

## Mejores prácticas

- **Mantenga los archivos enfocados**: un dominio por archivo
- **Utilice nombres claros**: `api-rest-conventions.md`, `testing-unit-patterns.md`
- **Incluir contexto**: explique *por qué* se tomaron las decisiones
- **Proporcione ejemplos**: use fragmentos de código y comparaciones antes/después
- **La seguridad es lo primero**: nunca incluya claves API ni datos confidenciales
- **Mantener regularmente**: trate los cambios de dirección como cambios de código

---

## Estrategias comunes de archivos de dirección

| Archivo | Contenido |
|---|---|
| `api-estándares.md` | Convenciones REST, formatos de respuesta de error, flujos de autenticación |
| `testing-standards.md` | Patrones de pruebas unitarias, estrategias de integración, burlas, cobertura |
| `código-convenciones.md` | Patrones de nombres, organización de archivos, decisiones arquitectónicas |
| `políticas-de-seguridad.md` | Requisitos de autenticación, validación de datos, codificación segura |
| `despliegue-flujo de trabajo.md` | Procedimientos de compilación, configuraciones del entorno, detalles de CI/CD |