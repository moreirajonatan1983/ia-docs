# Dirección

> **Fuente:** [kiro.dev/docs/steering/](https://kiro.dev/docs/steering/)

---

Los archivos de dirección guían la IA de Kiro con un contexto global o específico del espacio de trabajo a través de documentos de rebajas que definen sus estándares, arquitectura y convenciones, lo que le brinda a Kiro una comprensión persistente de cómo funciona su proyecto.

---

## ¿Qué es la dirección?

Los archivos de dirección son documentos de rebajas almacenados en `.kiro/steering/` que Kiro lee automáticamente durante las interacciones de chat. Proporcionan conocimiento específico del proyecto que da forma a las sugerencias, la generación de código y el comportamiento de Kiro.

**Beneficios clave:**
- Mantener una calidad de código consistente en todas las sesiones.
- Compartir convenciones de equipo automáticamente
- Reducir las correcciones repetitivas
- Habilitar experiencia en un dominio específico

---

## Alcance del archivo directivo

### Dirección del espacio de trabajo

Reside en `.kiro/steering/` en la raíz de tu espacio de trabajo. Aplicar solo a ese espacio de trabajo específico. Se utiliza para informar a Kiro sobre patrones, bibliotecas y estándares que se aplican a un espacio de trabajo individual.

### Dirección global

Reside en `~/.kiro/steering/` en tu directorio de inicio. Aplicar a **todos** los espacios de trabajo. Se utiliza para informar a Kiro sobre las convenciones que se aplican en todos sus proyectos.

> **Nota:** En caso de instrucciones contradictorias entre la dirección global y del espacio de trabajo, **la dirección del espacio de trabajo tiene prioridad**.

### Dirección del equipo

La dirección global puede distribuir archivos de dirección centralizados a equipos completos a través de soluciones MDM, políticas de grupo o descargándolos desde un repositorio central a `~/.kiro/steering`.

---

## Archivos directivos fundamentales

Haga clic en **Generar documentos de dirección** en el panel de Kiro para generar automáticamente tres archivos fundamentales:

| Archivo | Propósito |
|---|---|
| `producto.md` | Define el propósito de su producto, los usuarios objetivo, las características clave y los objetivos comerciales.
| `tecnología.md` | Marcos de documentos, bibliotecas, herramientas de desarrollo y limitaciones técnicas |
| `estructura.md` | Describe la organización de archivos, convenciones de nomenclatura, patrones de importación y decisiones arquitectónicas |

Estos archivos básicos se incluyen en cada interacción de forma predeterminada.

---

## Creación de archivos de dirección personalizados

1. Navegue a la sección **Dirección** en el panel Kiro.
2. Haga clic en el botón **+**
3. Seleccione el alcance: **espacio de trabajo** o **global**
4. Elija un nombre de archivo descriptivo (por ejemplo, `api-standards.md`)
5. Escriba su guía utilizando rebajas estándar y lenguaje natural.
6. Opcionalmente, utilice el botón **Refinar** para que Kiro mejore sus requisitos.

---

## Agentes.md

Kiro admite el estándar [AGENTS.md](https://agents.md/). Agregue archivos `AGENTS.md` a `~/.kiro/steering/` o a la carpeta raíz de su espacio de trabajo.

> **Nota:** Los archivos AGENTS.md están **siempre incluidos** y no admiten modos de inclusión.

---

## Modos de inclusión

Configure cuándo se cargan los archivos de dirección agregando el texto preliminar de YAML en la parte superior del archivo:

### Siempre incluido (predeterminado)
```yaml
---
inclusión: siempre
---
```
Cargado en cada interacción de Kiro. Ideal para: pila de tecnología, convenciones de codificación, políticas de seguridad.

### Inclusión condicional
```yaml
---
inclusión: fileMatch
fileMatchPattern: "componentes/**/*.tsx"
---
```
Se incluye solo cuando se trabaja con archivos que coinciden con el patrón. Múltiples patrones:
```yaml
---
inclusión: fileMatch
fileMatchPattern: ["**/*.ts", "**/*.tsx", "**/tsconfig.*.json"]
---
```
Ideal para: patrones de componentes, reglas de diseño de API, enfoques de prueba específicos para ciertos tipos de archivos.

### Inclusión manual
```yaml
---
inclusión: manual
---
```
Incluya bajo demanda haciendo referencia con `#steering-file-name` en el chat o mediante comandos de barra diagonal `/`. Ideal para: guías de solución de problemas, procedimientos de migración o documentación con mucho contexto.

### Inclusión automática
```yaml
---
inclusión: automático
nombre: api-diseño
Descripción: Patrones y convenciones de diseño de API REST. Úselo al crear o modificar puntos finales de API.
---
```
Se incluye automáticamente cuando su solicitud coincide con la descripción. También disponible como comandos de barra diagonal. Ideal para: orientación con mucho contexto que solo debe cargarse cuando sea relevante.

---

## Referencias de archivos

Enlace a archivos del espacio de trabajo en vivo para mantener la dirección actualizada:
```
#[[archivo:<nombre_archivo_relativo>]]
```

Ejemplos:
- `#[[archivo:api/openapi.yaml]]`
- `#[[archivo:componentes/ui/button.tsx]]`
- `#[[archivo:.env.ejemplo]]`

---

## Mejores prácticas

- **Mantenga los archivos enfocados**: un dominio por archivo (diseño, prueba e implementación de API)
- **Utilice nombres claros**: `api-rest-conventions.md`, `testing-unit-patterns.md`
- **Incluir contexto**: explique *por qué* se tomaron decisiones, no solo cuáles son los estándares.
- **Proporcione ejemplos**: use fragmentos de código y comparaciones antes/después
- **La seguridad es lo primero**: nunca incluya claves API, contraseñas ni datos confidenciales
- **Mantener periódicamente**: revisar durante la planificación del sprint y los cambios de arquitectura; Trate los cambios de dirección como cambios de código.

---

## Estrategias comunes de archivos de dirección

| Archivo | Contenido |
|---|---|
| `api-estándares.md` | Convenciones REST, formatos de respuesta de error, flujos de autenticación, estrategias de control de versiones |
| `testing-standards.md` | Patrones de pruebas unitarias, estrategias de integración, burlas, expectativas de cobertura |
| `código-convenciones.md` | Patrones de nombres, organización de archivos, ordenamiento de importaciones, decisiones arquitectónicas |
| `políticas-de-seguridad.md` | Requisitos de autenticación, validación de datos, desinfección de entradas, prevención de vulnerabilidades |
| `despliegue-flujo de trabajo.md` | Procedimientos de compilación, configuraciones del entorno, detalles de la canalización de CI/CD |