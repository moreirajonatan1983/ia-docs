# Related Questions

> **Source:** [kiro.dev/docs/billing/related-questions/](https://kiro.dev/docs/billing/related-questions/)

---

## What is a credit?

Un crédito es una unidad de trabajo en respuesta a prompts de usuario. Los créditos se miden al segundo decimal (mínimo 0.01 créditos por tarea).

| Tipo de tarea | Consumo estimado |
|---|---|
| Prompts simples | Menos de 1 crédito |
| Tareas complejas (Spec execution) | Más de 1 crédito |
| Auto (modelo default) | Base X |
| Sonnet 4 | 1.3X (30% más que Auto) |

---

## When does Kiro bill me?

Kiro factura en base a mes calendario (UTC). Los upgrades mid-month se facturan inmediatamente con la diferencia prorrateada. Los overages aparecen como ítems separados en la factura mensual.

---

## What happens when I reach the monthly limit?

- **Kiro Free:** Los requests se pausan hasta el próximo mes. No hay overages disponibles — podés upgradear para acceso inmediato.
- **Planes pagos:** Si los overages están habilitados, continuás trabajando. Si no, los requests se pausan. Podés upgradear en cualquier momento para acceso inmediato.

---

## How does proration work?

**Primera vez que upgradeas (Free → Paid):**
- Cargo prorrateado por días restantes del mes
- Acceso inmediato a los créditos completos del plan
- Si upgradeas de nuevo el mismo mes: se descuenta lo ya pagado y se cobra la diferencia prorrateada

**Upgrades posteriores (Paid → Higher Paid):**
- Cargo retroactivo por la diferencia de precio para todo el mes
- El uso del mes se recalcula bajo los límites del nuevo plan (podés evitar overages retroactivamente)

---

## What happens to bonus credits if I upgrade early?

Si estás dentro del período de prueba de 30 días con créditos bonus, esos créditos se transfieren al plan nuevo por el resto del período de 30 días.

---

## Near month-end: upgrade or enable overage?

- Si solo quedan pocos días, activar overages suele ser más simple
- Si el costo acumulado de overages se acerca a la diferencia de precio del siguiente plan, considerar upgradear
- En el primer mes pago, si upgradeas tarde, se aplica descuento por lo ya pagado

---

## Why might a single action cost more than one credit?

Algunos contextos son muy grandes (codebases extensas, tareas muy complejas), superando el límite de tokens de una sola request. Kiro lo cuenta como más de un crédito y muestra el total inmediatamente después de la interacción.

---

## How does Kiro optimize costs?

Kiro reusar contexto donde sea posible y aplica eficiencias como prompt caching y token-efficient tool use. Pagás por request, no por token, y las ganancias de eficiencia se reflejan en el diseño de precios.

---

## Which countries support paid plans?

Kiro actualmente soporta facturación en la mayoría de los países. Consultá la [lista completa en la documentación oficial](https://kiro.dev/docs/billing/related-questions/#which-countries-or-regions-are-supported-for-paid-plans). Se agregan más países regularmente.

---

## How can I retrieve my User ID?

![User Id](https://kiro.dev/videos/user-id.mp4)


Tu User ID está disponible en el **usage dashboard**. Aparece junto a tu email y método de inicio de sesión, con un ícono de copia para copiarlo fácilmente.