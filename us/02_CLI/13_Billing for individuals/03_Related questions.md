# Related Questions

> **Source:** [kiro.dev/docs/cli/billing/related-questions/](https://kiro.dev/docs/cli/billing/related-questions/)

---

## ¿Qué países/regiones soportan planes pagos?

Kiro soporta facturación en la mayoría de países del mundo incluyendo: Argentina, Brasil, Chile, Colombia, México, España, EE.UU., Canadá, Reino Unido, Alemania, Francia, Australia, Japón, India, y muchos más. Ver la lista completa en [kiro.dev/docs/cli/billing/related-questions/](https://kiro.dev/docs/cli/billing/related-questions/).

---

## ¿Qué es un credit?

Un **credit** es una unidad de trabajo en respuesta a prompts del usuario:
- Prompts simples: pueden consumir menos de 1 crédito
- Prompts complejos (ej. ejecutar una tarea spec): típicamente más de 1 crédito
- **Diferentes modelos consumen créditos a diferentes tasas** — Sonnet 4 cuesta 1.3x más créditos que Auto
- Los créditos se miden hasta el segundo decimal (mínimo: 0.01 créditos)

---

## ¿Qué plan pago elegir si no estoy seguro del uso futuro?

Recomendación: **empezar con Pro** y habilitar overage si es necesario. En el primer mes pago, si subís de plan, se aplica un descuento retroactivo desde el día que empezaste a pagar, sin penalización por esperar.

---

## ¿Qué plan elegir cuando mi uso ya es estable?

Elegí el **plan más pequeño que cubra un mes típico** con algo de margen:
- Sin overage: el uso se pausa al alcanzar el límite (factura predecible)
- Con overage habilitado: continuás trabajando sin interrupciones en picos ocasionales
- Si los picos son frecuentes o el costo de overage se acerca a la diferencia al siguiente tier, subir de plan suele ser más económico

---

## ¿Qué pasa cuando alcanzo el límite mensual de mi plan?

- **Free tier**: las requests se pausan hasta el inicio del próximo mes. No hay overage; podés upgradear para más capacidad inmediata.
- **Planes pagos**: podés habilitar overage para continuar trabajando sin interrupciones, o upgradear a un plan superior.

---

## ¿Cómo funciona la proratización en el primer upgrade?

En el primer mes que升级 a un plan pago, los cargos se prorratean por días restantes en el mes:
- Ejemplo: en un mes de 30 días, si upgradeas a Pro ($20) con 10 días restantes → pagás $6.67 (10/30 de $20) pero obtenés acceso completo a los límites del plan inmediatamente.
- Si en ese mismo mes subís a Pro+ ($40), se descuenta lo ya pagado y se cobra la diferencia.

---

## ¿Cómo funciona la proratización en upgrades posteriores?

La proratización **solo aplica al primer upgrade**. Después, cualquier upgrade en cualquier día del mes se cobra completo y el usuario recibe los límites completos del plan.

---

## ¿Cuándo factura Kiro?

Kiro factura en **mes calendario** (UTC). El cargo mensual exacto depende de tu zona horaria. Si upgradeas a mitad de mes, se cobra inmediatamente el costo del nuevo plan descontado el del anterior. El overage aparece como líneas separadas en la factura del mes.

---

## ¿Por qué una sola acción puede costar más de 1 crédito?

Algunas acciones requieren mucho más contexto o generan más output (ej. trabajar en un codebase grande o una build muy compleja). Cuando el uso total de tokens supera el límite de un solo request, Kiro lo cuenta como más de 1 crédito.

---

## ¿Cómo optimiza Kiro mis costos?

Kiro está diseñado para minimizar el trabajo redundante de LLM:
- Reutiliza contexto donde es posible
- Aplica eficiencias a nivel de proveedor (token-efficient tool use, prompt caching)
- **Pagás por request, no por token**
- Los beneficios de eficiencia se reflejan en el diseño de precios, no en la gestión manual de prompts