# Manage Subscriptions

> **Source:** [kiro.dev/docs/cli/enterprise/subscription-management/](https://kiro.dev/docs/cli/enterprise/subscription-management/)

---

## Change Kiro Subscription Plans

1. Iniciar sesión en **AWS Management Console**
2. Navegar a la **Kiro Console** (si no la ves, verificá la AWS Region)
3. Ir a **Users & Groups → Users o Groups tab**
4. Seleccionar el usuario o grupo
5. Elegir **Change plan** → seleccionar el nuevo plan → **Continue**

**Timing:**
- **Upgrade** (plan mayor): cambios **inmediatos**
- **Downgrade** (plan menor): cambios al **inicio del próximo mes**

Ver [Enterprise billing →](./09_Billing.md) para detalles sobre qué incluye cada tier.

---

## Unsubscribe Kiro Users

1. Iniciar sesión en **AWS Management Console**
2. Navegar a la **Kiro Console**
3. Ir a **Users & Groups → Users o Groups tab**
4. Seleccionar el usuario o grupo a cancelar
5. Elegir **Deactivate plan** → revisar el diálogo → **Unsubscribe**

> Después de cancelar, la suscripción se marca como **Canceled**. El usuario pierde acceso **inmediatamente** a las features pagas.

---

## Automatic Subscription Removal

Las suscripciones pueden removerse automáticamente cuando:
- Un usuario es removido del identity provider
- Un usuario es eliminado del grupo suscrito

---

## Enable Overages for Kiro Users

El overage permite a los usuarios continuar trabajando cuando superan los límites de su plan.

**Ventajas:**
- ✅ **Productividad ininterrumpida** durante picos de uso
- ✅ **Mejor comprensión del uso real** para dimensionar futuras suscripciones

**Por defecto, el overage está deshabilitado.** Una vez habilitado, aplica a **todos los usuarios y grupos del profile**.

Para habilitar:
1. Iniciar sesión en **AWS Management Console**
2. Navegar a la **Kiro Console**
3. Ir a **Settings**
4. En la sección **Kiro settings**, activar **Overages**

> Los caps personalizados de overage no están disponibles aún (próximamente).

---

## Subscription Statuses

| Estado | Descripción | ¿Se cobra? |
|---|---|---|
| **Active** | Suscrito y activo | ✅ Sí |
| **Canceled** | Cancelado por admin | ❌ No |
| **Pending** | Suscrito sin activar | ❌ No |