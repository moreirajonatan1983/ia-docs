# Mejores prácticas: especificaciones

> **Fuente:** [kiro.dev/docs/specs/best-practices/](https://kiro.dev/docs/specs/best-practices/)

---

## Especificaciones de funciones

### ¿Qué flujo de trabajo debo elegir?

Las especificaciones de funciones admiten dos flujos de trabajo: **Requisitos primero** y **Diseño primero**.

| Elija Requisitos: primero cuando... | Elija Diseño primero cuando... |
|---|---|
| Conoces el comportamiento del sistema que quieres construir | Tiene un diseño técnico o arquitectura existente |
| La arquitectura es flexible y puede diseñarse para satisfacer las necesidades | El sistema debe cumplir estrictos requisitos no funcionales |
| Creación de características de productos impulsadas por los comentarios de los clientes | Creación de prototipos con una pila tecnológica específica |
| Empezar sin limitaciones técnicas | Explorando la viabilidad técnica antes de comprometerse con el alcance |

### ¿Puedo cambiar los flujos de trabajo después de iniciar una especificación?

No, debes elegir un flujo de trabajo al crear la especificación. Si necesita cambiar los enfoques, cree una nueva especificación de función con el flujo de trabajo deseado. Puede copiar contenido relevante de la especificación anterior si es necesario.

### ¿Puedo utilizar ambos flujos de trabajo para el mismo proyecto?

¡Sí! Puede crear varias especificaciones. Por ejemplo:
1. Utilice Design-First para validar la viabilidad técnica
2. Cree una especificación de requisitos primero para el desarrollo completo de funciones.

### ¿Cómo importo diseños o arquitectura existentes?

- **Usando el flujo de trabajo Diseño-Primero:** Cree una nueva especificación de característica y seleccione Diseño-Primero, cargue diagramas de arquitectura (PNG, JPG) o pegue el contenido del diseño, Kiro formalizará el diseño en `design.md`.
- **Usar imágenes:** Exporte diagramas desde herramientas como draw.io, Lucidchart o tome fotografías de bocetos de pizarra e inclúyalas en su mensaje inicial.
- **Usando la integración MCP:** Si su herramienta de diseño tiene un [servidor MCP](https://kiro.dev/docs/mcp), puede conectarse directamente para importar diseños.

### ¿Cómo importo los requisitos existentes?

- **Usando la integración MCP:** Si su herramienta de requisitos tiene un servidor MCP (JIRA, Confluence, etc.), conéctese directamente para importar requisitos en su sesión de especificaciones.
- **Importación manual:** Copie sus requisitos existentes en un nuevo archivo en su repositorio y abra una sesión de chat de especificaciones:
  ```
  #foo-prfaq.md Genera una especificación a partir de él
  ```

### ¿Cómo repito mis especificaciones de funciones?

Continúe la sesión de chat de especificaciones para perfeccionar los requisitos, actualizar el diseño o ajustar las tareas. Kiro mantiene el contexto de su especificación durante toda la conversación.

---

## Especificaciones de corrección de errores

### ¿Cómo escribo una buena descripción de error?

Una descripción clara del error ayuda a Kiro a realizar un análisis preciso de la causa raíz. Incluir:

1. **Pasos de reproducción**: describe las condiciones exactas que desencadenan el error.
2. **Comportamiento actual**: lo que hace el sistema ahora (el defecto)
3. **Comportamiento esperado**: qué debería hacer el sistema en su lugar
4. **Restricciones**: cualquier código o comportamiento que no debe cambiar

**Ejemplo de mensaje:**
```
Cuando un usuario envía un formulario con caracteres especiales en el campo de nombre (por ejemplo, O'Brien),
la API devuelve un error 500. Debería aceptar la entrada y guardarla correctamente.
La lógica de validación de los campos de correo electrónico y contraseña no debería verse afectada.
```

### ¿Cómo evito regresiones con Bugfix Specs?

Las especificaciones de corrección de errores capturan explícitamente el "comportamiento sin cambios" junto con la corrección. Durante la fase de análisis documentar lo que se debe seguir trabajando:

```
- WHEN [condition] THEN the system SHALL CONTINUE TO [existing behavior]
```

Kiro genera pruebas basadas en propiedades que validan tanto la corrección como la preservación del comportamiento existente.

### ¿Cuándo debo utilizar una especificación de corrección de errores frente a una solución rápida?

**Utilice una especificación de corrección de errores cuando:**
- El error está en una ruta de código crítica.
- Los intentos de reparación anteriores provocaron regresiones.
- La causa raíz no es inmediatamente obvia.
- Necesita documentación para el cumplimiento o conocimiento del equipo.

**Una solución rápida en el chat está bien para:** errores tipográficos, errores lógicos simples o cambios de una línea bien entendidos.

### ¿Puedo convertir una especificación de corrección de errores en una especificación de función?

No directamente. Si el análisis de la causa raíz revela que la solución requiere una nueva funcionalidad significativa, cree una especificación de característica separada y mantenga la especificación de corrección de errores centrada en el defecto original.

---

## General

### ¿Cómo comparto especificaciones con mi equipo?

Las especificaciones están diseñadas para ser controladas por versiones. Almacene las especificaciones directamente en el repositorio de su proyecto junto con el código que describen. Esto mantiene todos los artefactos del proyecto juntos y mantiene la conexión entre los requisitos y la implementación.

### ¿Puedo compartir especificaciones entre varios equipos?

Sí, aprovechando los submódulos de Git o las referencias de paquetes:
1. Cree un repositorio central de especificaciones
2. Utilice submódulos de Git o referencias de paquetes para vincular especificaciones a proyectos individuales.
3. Implementar flujos de trabajo entre repositorios para proponer, revisar y actualizar especificaciones compartidas.

### ¿Puedo iniciar una sesión de especificaciones desde una sesión de vibración?

Sí. En una conversación de ambiente, diga "Generar especificaciones". Kiro te preguntará si deseas iniciar una sesión de especificaciones y generará requisitos basados ​​en el contexto de tu sesión de vibración.

### ¿Puedo ejecutar todas las tareas de mi especificación de una sola vez?

Sí. Haga clic en el botón **"Ejecutar todas las tareas"** en su archivo `tasks.md`. Nota: esto solo ejecutará tareas incompletas que estén marcadas como requeridas.

### ¿Qué pasa si algunas tareas ya están implementadas?

**Opción 1:** Haga clic en **"Actualizar tareas"** en su archivo `tasks.md`; Kiro marcará automáticamente las tareas completadas.

**Opción 2:** En una sesión de especificaciones, pregúntele a Kiro: *"Compruebe qué tareas ya están completas"*: Kiro analizará su código base y marcará las tareas completadas.

### ¿Cómo hago referencia a una especificación en el chat?

Utilice el proveedor de contexto `#spec`. Escriba `#spec` y presione Entrar para ver una lista de especificaciones disponibles, luego seleccione la que desea incluir. Kiro incluye automáticamente todos los archivos de especificaciones (`requirements.md`, `design.md` y `tasks.md`) en el contexto de la conversación.

### ¿Cuántas especificaciones puedo tener en un solo repositorio?

No hay un límite estricto. Organice las especificaciones de forma lógica dentro de `.kiro/specs/` usando nombres descriptivos para cada característica o corrección de errores.