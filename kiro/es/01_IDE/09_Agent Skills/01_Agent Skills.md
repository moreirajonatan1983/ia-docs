# Skills del agente

> **Fuente:** [kiro.dev/docs/skills/](https://kiro.dev/docs/skills/)

---

## ¿Qué son las skills?

Las **Skills** son paquetes de instrucciones portátiles que siguen el estándar abierto [Agent Skills](https://agentskills.io). Agrupan instrucciones, scripts y plantillas en paquetes reutilizables que Kiro puede activar cuando son relevantes para tu tarea.

Kiro soporta el estándar Agent Skills, por lo que podés:
- Importar skills de la comunidad o de otras herramientas de IA compatibles
- Comparte tus propias skills en el ecosistema.

---

## Cómo funcionan las skills

Las skills resuelven el problema del contexto excesivo usando **divulgación progresiva**:

| Etapa | Descripción |
|---|---|
| **1. Descubrimiento** | Al inicio, Kiro carga solo el nombre y descripción de cada skill |
| **2. Activación** | Cuando tu solicitud coincide con la descripción de una skill, Kiro carga las instrucciones completas |
| **3. Ejecución** | Kiro sigue las instrucciones, cargando scripts o archivos de referencia solo cuando es necesario |

Esto mantiene el contexto enfocado mientras da a Kiro acceso a conocimiento especializado extenso bajo demanda.

---

## Usando skills

Kiro activa automáticamente las skills cuando tu solicitud coincide con su descripción.

También podés invocar una skill directamente:
- Escribí `/` en el chat → las skills disponibles aparecen como comandos de barra diagonal
- Seleccioná un comando de barra diagonal → carga las instrucciones completas del Skill

Gestioná tus skills desde la sección **Steering y skills del agente** en el panel de Kiro.

---

## Alcance de la skill

| Alcance | Ubicación | Uso |
|---|---|---|
| **Espacio de trabajo** | `.kiro/skills/` | Solo el proyecto actual. Skills para flujos de trabajo específicos del proyecto (implementación, convenciones del equipo) |
| **Global** | `~/.kiro/skills/` | Disponible en todos los espacios de trabajo. Skills personales utilizadas en cualquier proyecto (revisión de código, documentación) |

> En caso de conflicto de nombres entre skills global y workspace, Kiro **prioriza el workspace skills**. Esto permite definir skills globales con posibilidad de sobreescribirlas por proyecto.

---

## Importación de skills

1. Abra la sección **Steering y skills del agente** en el panel de Kiro
2. Haga clic en **+** y seleccione **Importar una skill**
3. Elegí el origen:
   - **GitHub** — Importará desde una URL de repositorio público (apuntando a la carpeta del Skill o directamente al `SKILL.md`). La URL debe apuntar a un subdirectorio, no a la raíz del repositorio.
   - **Carpeta local** — Importá desde tu sistema de archivos

> Los skills importados se copian a tu directorio de skills y funcionan de inmediato.

---

## Creando una skill

Una skill es una carpeta que contiene un archivo `SKILL.md`:

```
my-skill/
├── SKILL.md          # Requerido
├── scripts/          # Opcional — código ejecutable
├── references/       # Opcional — documentación
└── assets/           # Opcional — templates
```

### Formato SKILL.md

```markdown
---
nombre: pr-revisión
Descripción: revise las pull requests para determinar la calidad del código, los problemas de seguridad y la cobertura de las pruebas.
             Úselo al revisar relaciones públicas o preparar código para revisión.
---

## Proceso de revisión
1. Verifique las vulnerabilidades de seguridad
2. Verificar el manejo de errores
3. Confirmar la cobertura de la prueba
4. Revisar el nombre y la estructura.
```

### Campos frontales

| Campo | Descripción |
|---|---|
| `nombre` | Identificador del Skill (usado como comando de barra diagonal) |
| `descripción` | Cuándo activar la skill — debe ser precisa y específica |
| `licencia` | Licencia del Skill (para distribución) |
| `compatibilidad` | Herramientas compatibles con IA |
| `metadatos` | Metadatos adicionales |

Ver la [especificación completa →](https://agentskills.io/specification)

---

## En qué se diferencian las skills de la dirección y los Powers

| Característica | Skills | Dirección | Powers |
|---|---|---|---|
| **Portabilidad** | ✅ Estándar abierto, compatibles | ❌ Específico de Kiro | ❌ Específico de Kiro |
| **Activación** | Bajo demanda (por descripción / comando de barra diagonal) | Siempre, automático, fileMatch, manual | Dinámica por contexto |
| **Guiones** | ✅ Puede incluir scripts ejecutables | ❌ No | Vía herramientas MCP |
| **Uso ideal** | Flujos de trabajo reutilizables para compartir | Convenciones y estándares del proyecto | Integraciones con herramientas + conocimiento |

> 💡 Para integraciones MCP, los **Powers** suelen ser la mejor opción — incluyen herramientas con guía integrada y se activan automáticamente.

---

## Mejores prácticas

- **Descripciones precisas** — Kiro las usa para decidir cuándo activar. Incluye palabras clave específicas: `"Revisar pull requests para seguridad y cobertura de pruebas"` > `"ayuda con la revisión del código"`
- **SKILL.md enfocado** — Poné documentación detallada en archivos `references/`. Kiro carga el SKILL.md completo en la activación
- **Scripts para tareas determinísticas** — Validación, generación de archivos y llamadas a APIs funcionan mejor como scripts que como código generado por LLM
- **Elegí el alcance correcto** — Global para flujos de trabajo personales; espacio de trabajo para procedimientos del equipo

---

## Relacionado

- [Dirección →](./03_Steering.md)
- [Powers →](./06_Powers/01_Install%20powers.md)
- [Especificación de skills del agente →](https://agentskills.io/specification)