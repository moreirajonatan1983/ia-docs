# Facturación empresarial

> **Fuente:** [kiro.dev/docs/enterprise/billing/](https://kiro.dev/docs/enterprise/billing/)

---

## Comparación de niveles

La facturación Enterprise es mensual por usuario suscrito. Para ver el detalle de precios por nivel: [kiro.dev/pricing/](https://kiro.dev/pricing/)

> Los planos y métodos de pago también se aplican a regiones **AWS GovCloud (US)**.

---

## Consideraciones de prorrateo

| Situación | Comportamiento |
|---|---|
| **Nueva suscripción a mitad de mes** | Carga prorrateada; acceso inmediato a los créditos completos del nivel |
| **Descripción mitad de mes** | Se paga el mes completo; la cancelación toma efecto el próximo mes |
| **Actualización a mitad de mes** | Reembolso del nivel inferior + carga completa del nivel superior. El mes se recalcula bajo los límites del nuevo nivel |
| **Rebaja de categoría a mitad de mes** | Se paga completo el nivel superior; el nivel inferior aplica desde el próximo mes |

> Actualizaciones → inmediatos. Degradaciones → inicio del siguiente mes.

---

## ¿Me facturarán dos veces?

**Perfil de Mismo Kiro:** Si un usuario está suscrito en dos grupos del mismo perfil, **no** se factura dos veces. Se paga el nivel más alto asignado al usuario.

**Diferente perfil de Kiro:** Si un usuario está suscrito en dos perfiles distintos (ej. dos regiones AWS diferentes), **sí** se factura dos veces.

---

## Ver su factura

- **AWS Billing and Cost Management** → pestaña **Cargos por servicio** → sección **Kiro**
- Para identificar costos por usuario: en **Exportaciones de datos**, creará una exportación con la opción **Incluir ID de recursos** activada

Recursos:
- [¿Qué es la gestión de costos y facturación de AWS? →](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-what-is.html)
- [Creación de exportaciones de datos →](https://docs.aws.amazon.com/cur/latest/userguide/dataexports-create.html)