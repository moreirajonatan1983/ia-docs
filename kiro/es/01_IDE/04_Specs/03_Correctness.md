# Corrección con pruebas basadas en propiedades

> **Fuente:** [kiro.dev/docs/specs/correctness/](https://kiro.dev/docs/specs/correctness/)

---

Kiro utiliza pruebas basadas en propiedades (PBT) para validar que su implementación realmente coincida con lo que definió en sus Specs. Este enfoque genera cientos o miles de casos de prueba automáticamente, detectando casos extremos que nunca escribiría manualmente.

---

## Conceptos

### ¿Qué es una propiedad?

Una propiedad es una **declaración universal** sobre cómo debe comportarse su sistema. Las propiedades expresan las invariantes y contratos que siempre deben ser verdaderos en su sistema, independientemente de los datos específicos involucrados.

> *"Para cualquier usuario autenticado y cualquier listado activo, el usuario puede ver ese listado."*

Esto captura una regla general sobre el comportamiento del sistema que debe cumplirse en todos los escenarios válidos. En el mundo de las Specs de Kiro, esto se corresponde directamente con los requisitos de EARS.

### Cómo funcionan las pruebas basadas en propiedades

**Prueba tradicional:**
- El usuario agrega el Auto #5 a favoritos → El Auto #5 aparece en su lista

**Prueba basada en propiedades:**
- CUANDO cualquier usuario agregue un automóvil a favoritos, EL Sistema LO mostrará en su lista

PBT prueba esto automáticamente con:
- Usuario A agregando el Auto #1
- Usuario B añadiendo el coche n.º 500
- Usuarios con caracteres especiales en los nombres.
- Coches con varios estados.
- Cientos de combinaciones más

Esto detecta casos extremos y verifica que la implementación coincida con la intención.

A lo largo de este proceso, PBT busca contraejemplos mediante la **"reducción"**, casi como un equipo rojo que intenta descifrar su código. Cuando encuentra infracciones, Kiro puede actualizar automáticamente su implementación o las opciones de superficie para corregir la spec, la implementación o la prueba.

---

## Pruebas basadas en propiedades con Specs

### Flujo de trabajo

Kiro extrae propiedades de sus requisitos formateados en EARS:

1. Identifica requisitos como *"EL Sistema DEBE permitir a los usuarios autenticados ver listados de automóviles activos"*
2. Determina qué propiedades se pueden probar lógicamente.
3. Genera cientos o miles de casos de prueba aleatorios cuando elige ejecutarlos.

### Fase de diseño

En la fase de diseño, Kiro:
- Extrae propiedades de sus requisitos.
- Genera casos de prueba.
- Al pasar el cursor sobre una propiedad se revela su conexión con el requisito original y la tarea vinculada.

### Ejecutando tareas

En la fase de ejecución, Kiro ejecuta los casos PBT generados en su implementación.

> **Nota:** Los PBT son **opcionales de forma predeterminada** para que pueda concentrarse primero en su implementación principal. Una vez que se ejecuta una prueba de propiedad, puede ver la referencia al código generado.

Cuando falla una prueba de propiedad, Kiro:
1. Identifica el escenario de falla específico y lo presenta para su revisión.
2. Te permite chatear con Kiro para entender el fallo.
3. Le permite determinar la solución adecuada, ya sea actualizando la implementación, ajustando la prueba o refinando el requisito en sí.