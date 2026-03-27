# Billing

> **Source:** [kiro.dev/docs/cli/enterprise/billing/](https://kiro.dev/docs/cli/enterprise/billing/)

---

## Enterprise Billing Overview

La facturación Enterprise de Kiro se gestiona a través de la **AWS Console**, a diferencia de los usuarios individuales que usan el portal de Kiro directamente.

---

## Subscription Tiers

Los administradores pueden suscribir usuarios a diferentes tiers según las necesidades del equipo. Cada tier incluye:
- Un número predeterminado de **Kiro credits** por mes
- Acceso a diferentes features según el plan

Ver [Pricing →](https://kiro.dev/pricing/) para la comparación actualizada de tiers y precios.

---

## How Enterprise Billing Works

- La facturación se realiza **por usuario suscrito activo** mensualmente
- Los usuarios con estado **Pending** (no activados) **no se cobran**
- Los cambios de plan toman efecto:
  - **Upgrades**: inmediatamente
  - **Downgrades**: al inicio del próximo mes

---

## Overages

Por defecto, los overages están **deshabilitados**. Los administradores pueden habilitarlos para permitir que los usuarios continúen trabajando al superar su límite mensual.

Para habilitar overages ver [Manage Subscriptions → Enable Overages →](./05_Manage subscriptions.md)

---

## Viewing Billing Information

Los administradores pueden ver:
- Dashboard de uso de la organización en la **Kiro Console**
- Actividad por usuario
- Costos de overage (si están habilitados)

---

## Contacting Billing Support

Para consultas de facturación Enterprise:
- [Billing support portal →](https://app.kiro.dev/account/usage?support_form)
- Email: [billing@kiro.dev](mailto:billing@kiro.dev)