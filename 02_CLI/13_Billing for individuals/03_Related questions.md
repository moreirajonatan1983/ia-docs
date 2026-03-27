# Preguntas relacionadas

> **Fuente:** [kiro.dev/docs/cli/billing/ related-questions/](https://kiro.dev/docs/cli/billing/ related-questions/)

---

## ¿Qué países/regiones soportan pagos de aviones?

Kiro soporta facturación en la mayoría de países del mundo incluyendo: Argentina, Brasil, Chile, Colombia, México, España, EE.UU., Canadá, Reino Unido, Alemania, Francia, Australia, Japón, India, y muchos más. Consulte la lista completa en [kiro.dev/docs/cli/billing/ related-questions/](https://kiro.dev/docs/cli/billing/ related-questions/).

---

## ¿Qué es un crédito?

Un **crédito** es una unidad de trabajo en respuesta a las indicaciones del usuario:
- Avisos simples: pueden consumir menos de 1 crédito
- Prompts complejos (ejemplo: ejecutar una tarea spec): sustancialmente más de 1 crédito
- **Diferentes modelos consumen créditos a diferentes tasas** — Sonnet 4 cuesta 1.3x más créditos que Auto
- Los créditos se miden hasta el segundo decimal (mínimo: 0.01 créditos)

---

## ¿Qué plan pago elegir si no estoy seguro del uso futuro?

Recomendación: **empezar con Pro** y habilitar overage si es necesario. En el primer mes pago, si subís de plan, se aplica un descuento retroactivo desde el día que empezaste a pagar, sin penalización por esperar.

---

## ¿Qué plan elegir cuando mi uso ya es estable?

Elegí el **plan más pequeño que abraza un mes típico** con algo de margen:
- Sin overage: el uso se pausa al alcanzar el límite (factura predecible)
- Con overage habilitado: continuás trabajando sin interrupciones en picos ocasionales
- Si los picos son frecuentes o el costo de excedente se acerca a la diferencia al siguiente nivel, subir de plan suele ser más económico

---

## ¿Qué pasa cuando alcanzo el límite mensual de mi plan?

- **Nivel gratuito**: las solicitudes se pausan hasta el inicio del próximo mes. No hay exceso de heno; Podés actualizar para más capacidad inmediata.
- **Planes pagos**: podrás habilitar el excedente para continuar trabajando sin interrupciones, o actualizar a un plan superior.

---

## ¿Cómo funciona la prorratización en el primer update?

En el primer mes que升级 a un plan pago, los cargos se prorratean por los días restantes en el mes:
- Ejemplo: en un mes de 30 días, si actualiza a Pro ($20) con 10 días restantes → paga $6.67 (10/30 de $20) pero obtendrás acceso completo a los límites del plan inmediatamente.
- Si en ese mismo mes subís a Pro+ ($40), se descuenta lo ya pagado y se cobra la diferencia.

---

## ¿Cómo funciona la prorratización en actualizaciones posteriores?

La prorratización **solo aplica al primer update**. Después, cualquier actualización en cualquier día del mes se cobra completo y el usuario recibe los límites completos del plan.

---

## ¿Cuándo factura Kiro?

Kiro factura en **mes calendario** (UTC). El cargo mensual exacto depende de tu zona horaria. Si actualizas a la mitad de mes, se cobra inmediatamente el costo del nuevo plan descontado el del anterior. El excedente aparece como líneas separadas en la factura del mes.

---

## ¿Por qué una sola acción puede costar más de 1 crédito?

Algunas acciones requieren mucho más contexto o generar más resultados (ej. trabajar en un código base grande o una construcción muy compleja). Cuando el uso total de tokens supera el límite de una sola solicitud, Kiro lo cuenta como más de 1 crédito.

---

## ¿Cómo optimizar Kiro mis costos?

Kiro está diseñado para minimizar el trabajo redundante de LLM:
- Reutilizar contexto donde sea posible
- Aplicación eficiencias a nivel de proveedor (uso eficiente de herramientas con token, almacenamiento en caché rápido)
- **Pagás por request, no por token**
- Los beneficios de eficiencia se reflejan en el diseño de precios, no en la gestión manual de avisos.