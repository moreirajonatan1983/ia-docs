# Specs

> **Fuente:** [kiro.dev/docs/specs/](https://kiro.dev/docs/specs/)

---

Las Specs o Specs son artefactos estructurados que formalizan el proceso de desarrollo de funciones y corrección de errores en su aplicación. Proporcionan un enfoque sistemático para transformar ideas de alto nivel en planes de implementación detallados con un seguimiento y una rendición de cuentas claros.

Con las Specs de Kiro, puedes:
- Dividir los requisitos en historias de usuarios con criterios de aceptación.
- Crear documentos de diseño con diagramas de secuencia y planos de arquitectura.
- Seguimiento del progreso de la implementación en tareas discretas
- Colaborar eficazmente entre los equipos de producto e ingeniería.

---

## Estructura central

Cada spec genera tres archivos clave:

| Archivo | Propósito |
|---|---|
| `requisitos.md` (o `bugfix.md`) | Captura historias de usuarios, criterios de aceptación o análisis de errores en notación estructurada |
| `diseño.md` | Documenta la arquitectura técnica, los diagramas de secuencia y las consideraciones de implementación.
| `tareas.md` | Proporciona un plan de implementación detallado con tareas discretas y rastreables |

---

## Flujo de trabajo trifásico

Todas las Specs siguen un flujo de trabajo de tres fases:

**1. Requisitos o análisis de errores**: defina lo que se debe crear o corregir
- Specs de funciones: historias de usuarios y criterios de aceptación en `requirements.md`
- Specs de corrección de errores: análisis de errores con comportamiento actual/esperado/sin cambios en `bugfix.md`

**2. Diseño**: cree una arquitectura técnica y un enfoque de implementación en `design.md`
- Arquitectura del sistema y diseño de componentes.
- Diagramas de secuencia y flujo de datos.
- Manejo de errores y estrategia de prueba.

**3. Tareas**: genera tareas de implementación discretas y ejecutables en `tasks.md`
- Tareas rastreables con resultados claros
- Actualizaciones de estado en tiempo real a medida que implementas
- Ejecutar tareas individualmente o todas a la vez

---

## Ejecución de tareas

Kiro proporciona una interfaz de ejecución de tareas para archivos `tasks.md` que muestra actualizaciones de estado en tiempo real. Las tareas se actualizan como en progreso o completadas, lo que le permite realizar un seguimiento eficiente del progreso de la implementación.

---

## Tipos de Specs

| Tipo | Lo mejor para |
|---|---|
| **Specs de funciones** | Nuevas características que requieren planificación estructurada y requisitos EARS |
| **Specs de corrección de errores** | Corrección de errores con precisión quirúrgica y evitando regresiones |

---

## Empezando

1. Desde el panel Kiro, haga clic en el botón **+** debajo de Specs. Alternativamente, elija **spec** en el panel de chat.
2. Kiro te preguntará si estás desarrollando una **Función** o solucionando un **Error**
   - Si elige **Función**, describa su función y elija su flujo de trabajo: Requisitos primero o Diseño primero
   - Si elige **Error**, describa su error.
3. Siga el flujo de trabajo en cada fase hasta la implementación.

---

## Cuándo utilizar Specs frente a Vibe

| Utilizá Specs cuando... | Utilizá Vibe cuando... |
|---|---|
| Construcción de características complejas que requieren una planificación estructurada | Codificación exploratoria rápida |
| Corrección de errores en los que las regresiones son costosas | Prototipos sin objetivos claros |
| Necesitas documentación para compartir con tu equipo | |
| Requiere iterar fuertemente sobre el diseño y la lógica | |

---

## Más información

- [Specs de funciones →](https://kiro.dev/docs/specs/feature-specs/)
- [Specs de corrección de errores →](https://kiro.dev/docs/specs/bugfix-specs/)
- [Mejores prácticas →](https://kiro.dev/docs/specs/best-practices/)