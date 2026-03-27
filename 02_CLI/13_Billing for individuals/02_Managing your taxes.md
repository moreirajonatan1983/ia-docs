# Administrar sus impuestos

> **Fuente:** [kiro.dev/docs/cli/billing/managing-taxes/](https://kiro.dev/docs/cli/billing/managing-taxes/)

---

## ¿Por qué veo Amazon Web Services, Inc. en mi compra de Kiro?

Amazon Web Services, Inc. (AWSI) es el proveedor de servicios de Kiro. AWSI:
- Está establecido y opera en Estados Unidos
- Está registrado para Impuesto sobre las Ventas en los estados correspondientes
- Está registrado para IVA en países donde las leyes de impuestos indirectos requieren que proveedores extranjeros de Servicios Suministrados Electrónicamente (ESS) se registren y cobren IVA local.

AWSI trata a Kiro como:
- **Software descargado** en EE. UU.
- **ESS (Servicios suministrados electrónicamente)** fuera de EE.UU.

---

## ¿Cómo determina AWS mi ubicación para los impuestos?

AWS usará la **dirección de facturación del cliente** provista al comprar Kiro. Si la dirección es inválida, recibirá un error `customer_tax_location_invalid`.

---

## Clientes B2B e IVA (cargo revertido)

Si sos cliente B2B y ya tenés un TRN (Número de Registro Fiscal) en tu cuenta AWS, **igualmente necesitás agregarlo a tu cuenta Kiro** a través del portal de clientes de forma separada.

En ciertas jurisdicciones, AWS debe cobrar y recolectar impuestos tanto en compras B2B como B2C.

---

## Actualización de información fiscal a mitad de mes

AWS usará tu dirección de facturación al momento de la compra, o al momento de cambios en tu suscripción (upgrades o renovaciones).

---

## Métodos de pago y monedas

| Métodos aceptados | Moneda |
|---|---|
| Todas las tarjetas de crédito principales | USD únicamente |

---

## Problemas con facturas con IVA

Si tu factura de IVA o el vendedor de AWS aparece incorrectamente, contacta al [soporte de billing de Kiro](https://app.kiro.dev/account/usage?support_form).

---

## Números de Registro Tributario (TRN)

Kiro acepta TRN según los requisitos del país del cliente. Al agregar un TRN, Kiro verificará que el formato sea correcto.

> **Nota:** El estado especial de exención de IVA (para organizaciones con status de alivio) estará disponible próximamente.