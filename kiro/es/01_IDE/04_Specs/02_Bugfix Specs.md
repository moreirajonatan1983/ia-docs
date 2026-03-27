# Specs de corrección de errores

> **Fuente:** [kiro.dev/docs/specs/bugfix-specs/](https://kiro.dev/docs/specs/bugfix-specs/)

---

Bugfix Specs proporciona un enfoque estructurado para diagnosticar y corregir errores sistemáticamente con precisión quirúrgica y al mismo tiempo prevenir regresiones.

---

## Beneficios clave

| Beneficio | Descripción |
|---|---|
| **Correcciones quirúrgicas** | Las restricciones explícitas garantizan que sólo se realicen los cambios necesarios |
| **Prevención de regresión** | El comportamiento sin cambios está documentado y probado |
| **Documentación** | Registro completo del error, corrección y razonamiento para referencia futura |
| **Confiabilidad** | El flujo de trabajo estructurado evita los errores comunes de las correcciones ad hoc |

---

## Cuándo utilizar las Specs de corrección de errores

Lo mejor para:
- Errores complejos que requieren análisis de causa raíz
- Errores en rutas de código críticas donde las regresiones son costosas
- Errores que necesitan documentación para cumplimiento o conocimiento del equipo.
- Situaciones en las que intentos de reparación anteriores provocaron regresiones

---

## Cómo funciona

Las Specs de corrección de errores siguen el mismo flujo de trabajo de tres fases que las Specs de funciones (Requisitos → Diseño → Tareas), pero con contenido diseñado para correcciones de errores quirúrgicos:

### 1. Fase de análisis de corrección de errores

En lugar de un documento de requisitos, crea un `bugfix.md` que captura:

```
Comportamiento actual (defecto)
- CUANDO [condición] ENTONCES el sistema [comportamiento incorrecto]

Comportamiento esperado (correcto)
- CUANDO [condición] ENTONCES el sistema DEBE [comportamiento correcto]

Comportamiento sin cambios (prevención de regresión)
- CUANDO [condición] ENTONCES el sistema CONTINUARÁ CON [comportamiento existente]
```

Esta estructura explícita garantiza que Kiro comprenda no sólo lo que está roto, sino también lo que debe seguir funcionando.

### 2. Fase de diseño

Kiro explora el código base para encontrar la causa raíz del problema y genera un `design.md` con:
- Análisis de causa raíz
- Enfoque de solución propuesto
- Propiedades a probar:
  - La implementación actual produce un comportamiento incorrecto *(valida la existencia del error)*
  - La implementación fija produce un comportamiento correcto *(valida que la solución funciona)*
  - La implementación sin cambios continúa funcionando *(evita regresiones)*

### 3. Fase de Tareas

Las tareas de implementación se generan con [pruebas basadas en propiedades (PBT)](https://kiro.dev/docs/specs/correctness) que validan:
- El error es reproducible.
- El error está arreglado.
- No se introducen regresiones.

---

## Empezando

1. Elija **spec** en el panel de chat.
2. Describe el error, incluyendo:
   - Cuando ocurre el error (pasos de reproducción)
   - ¿Qué debería pasar en su lugar?
   - Cualquier restricción (código que no debe modificarse)
3. Elige **Corrección de error** cuando Kiro te pregunte cuál es tu intención.
4. Siga el flujo de trabajo a través del análisis, diseño e implementación.

---

## Más información

- [Mejores prácticas para Specs de corrección de errores →](https://kiro.dev/docs/specs/best-practices/#bugfix-specs)
- [Corrección con pruebas basadas en propiedades →](https://kiro.dev/docs/specs/correctness/)