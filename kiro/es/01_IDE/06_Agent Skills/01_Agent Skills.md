# Skills del agente

> **Fuente:** [kiro.dev/docs/skills/](https://kiro.dev/docs/skills/)

---

Las skills son paquetes de instrucciones portátiles que siguen el estándar abierto [Agent Skills](https://agentskills.io). Incluyen instrucciones, scripts y plantillas en paquetes reutilizables que Kiro puede activar cuando sea relevante para su tarea.

Kiro admite el estándar Agent Skills, por lo que puedes importar skills de la comunidad u otras herramientas de IA compatibles y compartir tus propias skills en todo el ecosistema.

---

## ¿Qué son las skills?

Las skills resuelven la tensión entre **muy poco contexto** (los agentes adivinan) y **demasiado contexto** (los agentes disminuyen la velocidad) a través de la **divulgación progresiva**:

1. **Descubrimiento**: al inicio, Kiro carga solo el nombre y la descripción de cada skill.
2. **Activación**: cuando tu solicitud coincide con la descripción de una skill, Kiro carga las instrucciones completas.
3. **Ejecución**: Kiro sigue las instrucciones y carga scripts o archivos de referencia solo según sea necesario.

Esto mantiene el contexto enfocado y al mismo tiempo le brinda a Kiro acceso a un amplio conocimiento especializado bajo demanda.

---

## Cómo funcionan las skills

Sin conocimiento del proceso de implementación de su equipo, los estándares de revisión de código de su empresa o el proceso de análisis de datos de su proyecto, los agentes adivinan e iteran, tal como lo haría usted cuando aprende algo nuevo. Cargar todo este contexto por adelantado no es práctico.

Las skills resuelven esto cargando las instrucciones completas de las skills solo cuando Kiro determina que tu solicitud coincide con el propósito de una skill.

---

## Usando skills

Kiro **activa skills automáticamente** cuando tu solicitud coincide con la descripción de una skill.

También puedes invocar una skill directamente: escribe `/` en la entrada del chat para ver las skills disponibles como **comandos de barra diagonal**. Al seleccionar un comando de barra diagonal se cargan las instrucciones de skill completas.

Vea y administre skills en la sección **Steering y skills del agente** en el panel de Kiro.

---

## Alcance de la skill

| Alcance | Ubicación | Mejor para |
|---|---|---|
| **Workspace** | `.kiro/skills/` en la raíz del proyecto | Procedimientos de equipo, flujos de trabajo específicos de proyectos |
| **Global** | `~/.kiro/skills/` en el directorio de inicio | Flujos de trabajo personales, hábitos entre proyectos |

---

## Importación de skills

1. Abrí la sección **Steering y skills del agente** en el panel de Kiro.
2. Hacé clic en **+** y seleccione **Importar una skill**
3. Elige tu fuente:
   - **GitHub** — Importar desde una URL de repositorio público (pegue la URL que apunta a la carpeta de skills o directamente al archivo `SKILL.md`). La URL debe apuntar a un subdirectorio, no a la raíz del repositorio.
   - **Carpeta local** — Importar desde su sistema de archivos

Las skills importadas se copian en su directorio de skills y funcionan inmediatamente.

---

## Creando una skill

Una skill es una carpeta que contiene un archivo `SKILL.md`:

```
my-skill/
├── SKILL.md        # Required
├── scripts/        # Optional executable code
├── references/     # Optional documentation
└── assets/         # Optional templates
```

### Formato SKILL.md

```markdown
---
nombre: pr-revisión
Descripción: revise las pull requests para determinar la calidad del código, los problemas de seguridad y la cobertura de las pruebas. Úselo al revisar Pull Requests o preparar código para revisión.
---

## Proceso de revisión

1. Verifique las vulnerabilidades de seguridad
2. Verificar el manejo de errores
3. Confirmar la cobertura de la prueba
4. Revisar el nombre y la estructura.
```

### Campos frontales

| Campo | Requerido | Descripción |
|---|---|---|
| `nombre` | ✅ | Identificador de skill (usado como comando de barra diagonal) |
| `descripción` | ✅ | Utilizado por Kiro para decidir cuándo activar |
| `licencia` | ✗ | Identificador de licencia SPDX |
| `compatibilidad` | ✗ | Herramientas de IA compatibles |
| `metadatos` | ✗ | Metadatos clave/valor adicionales |

Consulte la [spec completa →](https://agentskills.io/specification)

---

## En qué se diferencian las skills de la dirección y los Powers

| Característica | Skills | Dirección | Powers |
|---|---|---|---|
| **Estándar** | Abierto (spec de skills del agente) | Específico de Kiro | Específico de Kiro |
| **Cargando** | Bajo demanda | siempre/auto/fileMatch/manual | Dinámico basado en el contexto |
| **scripts** | ✅ Sí | ✗ No | ✅ Sí |
| **Herramientas MCP** | ✗ No | ✗ No | ✅ Sí |
| **Mejor para** | Flujos de trabajo reutilizables para compartir o importar | Estándares y convenciones de proyectos | Integraciones de MCP con conocimientos agrupados |

> Para las integraciones de MCP, [Powers](https://kiro.dev/docs/powers) suelen ser una mejor opción: combinan herramientas con orientación integrada y se activan automáticamente.

---

## Mejores prácticas

- **Escribe descripciones precisas**: Kiro usa la descripción para decidir cuándo activar. Incluya palabras clave específicas: "Revisar las pull requests para seguridad y cobertura de pruebas" supera a "ayuda con la revisión del código".
- **Mantenga enfocado SKILL.md**: coloque documentación detallada en archivos `referencias/`. Kiro carga el `SKILL.md` completo al activarlo.
- **Utilizá secuencias de comandos para tareas deterministas**: la validación, la generación de archivos y las llamadas API funcionan mejor como secuencias de comandos que el código generado por LLM.
- **Elija el alcance correcto**: global para flujos de trabajo personales (su lista de verificación de revisión), Workspace para procedimientos de equipo (implementación de proyectos).

---

## Documentación relacionada

- [Dirección →](https://kiro.dev/docs/steering) — Contexto y estándares específicos del proyecto
- [Powers →](https://kiro.dev/docs/powers) — Integraciones de MCP con conocimientos incluidos
- [spec de skills del agente →](https://agentskills.io/specification)