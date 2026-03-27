# Indexación de base de código

> **Fuente:** [kiro.dev/docs/editor/codebase-indexing/](https://kiro.dev/docs/editor/codebase-indexing/)

---

Kiro indexa su código base para brindar asistencia de código inteligente y contextual. Comprender cómo funciona la indexación le ayudará a aprovechar al máximo las funciones de IA de Kiro.

---

## Cuando se produce la indexación

### Indexación automática

Kiro realiza la indexación automáticamente en estos escenarios:

1. **Importación de proyectos**: cuando abres un proyecto por primera vez en Kiro, automáticamente comienza a indexar todos los archivos en tu espacio de trabajo.
2. **Cambios de archivos**: cuando se crean o agregan nuevos archivos a su proyecto, se indexan automáticamente.
3. **Cambios externos**: cuando los archivos se modifican fuera de Kiro (por ejemplo, mediante operaciones de git), se vuelven a indexar.

### Indexación manual

Puede activar la indexación manualmente cuando sea necesario usando la **Paleta de comandos**:
- macOS: `Cmd+Mayús+P`
- Windows/Linux: `Ctrl+Mayús+P`

---

## Comandos de indexación disponibles

![Indexación de Kiro](https://kiro.dev/images/kiro-indexing.png)

### Indexación de base de código

| Comando | Cuándo utilizar |
|---|---|
| `Kiro: Reindexación de la fuerza del código base` | Fuerza una reindexación completa de todo el código base. Utilícelo cuando: el índice parezca corrupto o incompleto, se hayan realizado cambios estructurales importantes o las sugerencias parezcan obsoletas. |
| `Kiro: Reconstruir el índice base del código` | Reconstruye completamente el índice de la base de código desde cero. Más completo que forzar la reindexación. Utilícelo cuando el índice parezca muy dañado o experimente problemas persistentes. |

### Indexación de documentación

| Comando | Descripción |
|---|---|
| `Kiro: Índice de documentos` | Inicia la indexación de archivos de documentación en su proyecto |
| `Kiro: Docs fuerza la reindexación` | Fuerza una reindexación completa de todos los archivos de documentación |

---

## Monitoreo del progreso de la indexación

![Registros de indexación de Kiro](https://kiro.dev/images/kiro-indexing-logs.png)

Puedes monitorear el proceso de indexación a través del panel **Kiro Logs**:

1. Accede al panel **Salida** en Kiro
2. Seleccione **"Kiro Logs"** en el menú desplegable.
3. Vea el progreso de la indexación y las actualizaciones de estado en tiempo real.

Los registros muestran:
- Cuando comienza y finaliza la indexación.
- Número de archivos encontrados y procesados.
- Porcentaje de progreso para grandes bases de código
- Tiempo de finalización de las operaciones de indexación.

---

## Contenido indexado

Kiro indexa varios tipos de contenido para brindar asistencia inteligente:

| Tipo de contenido | Ejemplos |
|---|---|
| **Código fuente** | Todos los archivos de lenguajes de programación en su espacio de trabajo |
| **Documentación** | Markdown, MDX y otros formatos de documentación |
| **Configuración** | Archivos de configuración del proyecto y manifiestos |
| **Dependencias** | Definiciones de paquetes e información de dependencia |

Los datos indexados permiten funciones como:
- Finalización de código inteligente
- Navegación entre archivos
- Sugerencias contextuales
- Búsqueda de documentación.
- Asistencia de refactorización de código