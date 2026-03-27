# Preguntas relacionadas

> **Fuente:** [kiro.dev/docs/billing/ related-questions/](https://kiro.dev/docs/billing/ related-questions/)

---

## ¿Qué es un crédito?

Un crédito es una unidad de trabajo en respuesta a avisos de usuario. Los créditos se miden al segundo decimal (mínimo 0.01 créditos por tarea).

| Tipo de tarea | Consumo estimado |
|---|---|
| Indicaciones simples | Menos de 1 crédito |
| Tareas complejas (Ejecución Spec) | Más de 1 crédito |
| Auto (modelo predeterminado) | Base X |
| Soneto 4 | 1.3X (30% más que Auto) |

---

## ¿Cuándo me factura Kiro?

Kiro factura en base a mes calendario (UTC). Los actualizaciones a mitad de mes se facturan inmediatamente con la diferencia prorrateada. Los excedentes aparecen como artículos separados en la factura mensual.

---

## ¿Qué pasa cuando llego al límite mensual?

- **Kiro Free:** Las solicitudes se pausan hasta el próximo mes. No hay excedentes disponibles: podés actualizar para acceso inmediato.
- **Pagos de aviones:** Si los excedentes están habilitados, continúa trabajando. Si no, las solicitudes se pausan. Podés actualizar en cualquier momento para acceso inmediato.

---

## ¿Cómo funciona el prorrateo?

**Primera vez que actualizas (Gratis → Pagado):**
- Carga prorratada por los días restantes del mes
- Acceso inmediato a los créditos completos del plan
- Si actualizas de nuevo el mismo mes: se descuenta lo ya pagado y se cobra la diferencia prorrateada

**Actualizaciones posteriores (Pagadas → Mejor pagadas):**
- Cargo retroactivo por la diferencia de precio para todo el mes
- El uso del mes se recalcula bajo los límites del nuevo plan (podés evitar excedentes retroactivamente)

---

## ¿Qué sucede con los créditos de bonificación si actualizo antes?

Si estás dentro del período de prueba de 30 días con créditos bonus, esos créditos se transferirán al plan nuevo por el resto del período de 30 días.

---

## Cerca de fin de mes: ¿actualizar o habilitar el excedente?

- Si solo quedan pocos días, activar excedentes suele ser más simple
- Si el costo acumulado de excedentes se acerca a la diferencia de precio del siguiente plan, considere actualizar
- En el primer mes pago, si actualizas tarde, se aplica descuento por lo ya pagado

---

## ¿Por qué una sola acción podría costar más de un crédito?

Algunos contextos son muy grandes (bases de código extensas, tareas muy complejas), superando el límite de tokens de una sola solicitud. Kiro lo cuenta como más de un crédito y muestra el total inmediatamente después de la interacción.

---

## ¿Cómo optimiza Kiro los costes?

Kiro reusar contexto donde sea posible y eficiencias de aplicaciones como almacenamiento en caché rápido y uso eficiente de herramientas de token. Pagás por request, no por token, y las ganancias de eficiencia se reflejan en el diseño de precios.

---

## ¿Qué países admiten planes pagos?

Kiro actualmente soporta facturación en la mayoría de los países. Consulta la [lista completa en la documentación oficial](https://kiro.dev/docs/billing/ related-questions/#what-countries-or-regions-are-supported-for-paid-plans). Se agregarán más países regularmente.

---

## ¿Cómo puedo recuperar mi ID de usuario?

![Identificación de usuario](https://kiro.dev/videos/user-id.mp4)

Tu ID de usuario está disponible en el **panel de uso**. Aparece junto a tu correo electrónico y método de inicio de sesión, con un ícono de copia para copiarlo fácilmente.