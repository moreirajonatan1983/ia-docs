# Managing Your Taxes

> **Source:** [kiro.dev/docs/cli/billing/managing-taxes/](https://kiro.dev/docs/cli/billing/managing-taxes/)

---

## Why do I see Amazon Web Services, Inc. on my Kiro purchase?

Amazon Web Services, Inc. (AWSI) es el proveedor de servicios de Kiro. AWSI:
- Está establecida y opera en Estados Unidos
- Está registrada para Sales Tax en los estados correspondientes
- Está registrada para IVA en países donde las leyes de impuestos indirectos requieren que proveedores extranjeros de Electronically Supplied Services (ESS) se registren y cobren IVA local

AWSI trata a Kiro como:
- **Downloaded Software** en USA
- **ESS (Electronically Supplied Services)** fuera de USA

---

## How does AWS determine my location for taxes?

AWS usará la **dirección de facturación del cliente** provista al comprar Kiro. Si la dirección es inválida, recibirás un error `customer_tax_location_invalid`.

---

## B2B customers and VAT (reverse charge)

Si sos cliente B2B y ya tenés un TRN (Tax Registration Number) en tu cuenta AWS, **igualmente necesitás agregarlo a tu cuenta Kiro** a través del portal de clientes de forma separada.

En ciertas jurisdicciones, AWS debe cobrar y recolectar impuestos tanto en compras B2B como B2C.

---

## Updating tax information mid-month

AWS usará tu dirección de facturación al momento de la compra, o al momento de cambios en tu suscripción (upgrades o renovaciones).

---

## Payment Methods and Currencies

| Métodos aceptados | Moneda |
|---|---|
| Todas las tarjetas de crédito principales | USD únicamente |

---

## VAT Invoice Issues

Si tu factura de IVA o el vendedor de AWS aparece incorrectamente, contacta al [soporte de billing de Kiro](https://app.kiro.dev/account/usage?support_form).

---

## Tax Registration Numbers (TRN)

Kiro acepta TRNs según los requisitos del país del cliente. Al agregar un TRN, Kiro verificará que el formato sea correcto.

> **Nota:** El estado especial de exención de IVA (para organizaciones con relief status) estará disponible próximamente.