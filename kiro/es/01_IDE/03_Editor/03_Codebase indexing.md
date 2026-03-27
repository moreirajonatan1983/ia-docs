# Indexación del código base

> **Fuente:** [kiro.dev/docs/editor/codebase-indexing/](https://kiro.dev/docs/editor/codebase-indexing/)

---

Kiro indexa tu código base para brindarte asistencia de código inteligente y contextual pura. Comprender cómo funciona la indexación por abajo te va a ayudar a exprimir las funciones de IA.

---

## Cuándo ocurre la indexación

### Indexación automática

Kiro arranca la indexación automáticamente en estos tres escenarios:

1. **Importación de proyectos:** Cuando abrís un proyecto por primera vez, Kiro comienza inmediatamente a indexar todos los archivos de tu *workspace*.
2. **Cambios de archivos:** Cuando creás o agregás nuevos archivos a tu proyecto, son indexados automáticamente al instante.
3. **Cambios externos:** Cuando los archivos se modifican por fuera del editor (por ejemplo, tirando un `git pull` en la consola), se vuelven a indexar.

### Indexación manual

Podés disparar la indexación a mano cuando lo creas necesario abriendo la **Paleta de Comandos**:
- macOS: `Cmd+Shift+P`
- Windows/Linux: `Ctrl+Shift+P`

---

## Comandos de indexación disponibles

![Kiro Indexing](https://kiro.dev/images/kiro-indexing.png)

### Indexación de la base de código

| Comando | Cuándo utilizar |
|---|---|
| `Kiro: Force Reindex Codebase` | Fuerza una reindexación completa de todo tu código base. Usalo cuando el índice parezca corrupto o incompleto, si hiciste cambios estructurales masivos de golpe, o si sentís que las sugerencias de la IA huelen a código viejo. |
| `Kiro: Rebuild Codebase Index` | Destruye y reconstruye completamente el índice desde cero. Es más agresivo y destructivo que forzar la reindexación normal. Usalo cuando el índice esté roto a otro nivel o si tenés dolores de cabeza persistentes de contexto. |

### Indexación de la documentación

| Comando | Descripción |
|---|---|
| `Kiro: Index Docs` | Inicia la indexación explícita de archivos de documentación. |
| `Kiro: Force Reindex Docs` | Fuerza una reindexación completa solo de los archivos documentales. |

---

## Cómo monitorear el progreso

![Kiro Indexing Logs](https://kiro.dev/images/kiro-indexing-logs.png)

Podés monitorear en qué estado anda el indexador abriendo el panel de **Kiro Logs**:

1. Accedé a la pestaña **Output** (Salida) del editor.
2. Seleccioná **"Kiro Logs"** en el menú desplegable de la pestaña.
3. Ahí vas a ver el progreso y todo lo que la maquinita procesa en tiempo real.

Los logs te detallan:
- Cuándo arranca y termina de indexar.
- Conteo de archivos encontrados y procesados vivos.
- Porcentajes para bases de código gigantes.
- Tiempos de latencia de las operaciones.

---

## Qué contenido se indexa

Kiro examina varios tipos de contenido para hacerte la vida fácil:

| Tipo de contenido | Ejemplos |
|---|---|
| **Código fuente** | Todos los lenguajes de programación en tu *workspace*. |
| **Documentación** | Archivos de texto Markdown, MDX, etc. |
| **Configuración** | Manifiestos, JSONs, y configuración global. |
| **Dependencias** | Definiciones de tus paquetes y dependencias clave. |

Toda esta data cruda alimenta:
- El autocompletado inteligente.
- La navegación veloz a través de todo tu árbol.
- Sugerencias que toman cuenta de archivos ajenos.
- Asistencia directa al encarar un *refactor* rudo de código.