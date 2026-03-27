# Enterprise Billing

> **Source:** [kiro.dev/docs/enterprise/billing/](https://kiro.dev/docs/enterprise/billing/)

---

## Tier Comparison

La facturación Enterprise es mensual por usuario suscripto. Para ver el detalle de precios por tier: [kiro.dev/pricing/](https://kiro.dev/pricing/)

> Los planes y métodos de pago también aplican a regiones **AWS GovCloud (US)**.

---

## Proration Considerations

| Situación | Comportamiento |
|---|---|
| **Nueva suscripción mid-month** | Cargo prorrateado; acceso inmediato a los créditos completos del tier |
| **Desuscripción mid-month** | Se paga el mes completo; la cancelación toma efecto el próximo mes |
| **Upgrade mid-month** | Reembolso del tier inferior + cargo completo del tier superior. El mes se recalcula bajo los límites del nuevo tier |
| **Downgrade mid-month** | Se paga completo el tier superior; el tier inferior aplica desde el próximo mes |

> Upgrades → inmediatos. Downgrades → inicio del siguiente mes.

---

## Will I be double-billed?

**Mismo Kiro profile:** Si un usuario está suscripto en dos grupos del mismo profile, **no** se factura dos veces. Se paga el tier más alto asignado al usuario.

**Diferente Kiro profile:** Si un usuario está suscripto en dos profiles distintos (ej. dos regiones AWS diferentes), **sí** se factura dos veces.

---

## Viewing Your Bill

- **AWS Billing and Cost Management** → pestaña **Charges by service** → sección **Kiro**
- Para identificar costos por usuario: en **Data Exports**, creá un export con la opción **Include resource IDs** activada

Recursos:
- [What is AWS Billing and Cost Management? →](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-what-is.html)
- [Creating data exports →](https://docs.aws.amazon.com/cur/latest/userguide/dataexports-create.html)