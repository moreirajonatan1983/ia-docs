# Managing Your Kiro CLI Subscription

> **Source:** [kiro.dev/docs/cli/billing/subscription-portal/](https://kiro.dev/docs/cli/billing/subscription-portal/)

---

## Accessing the Subscription Portal

Accedé al portal en: **[app.kiro.dev/account/usage](https://app.kiro.dev/account/usage)**

Desde el CLI, usá el comando `/usage` para ver el link al portal.

```
> /usage
```

---

## What You Can Do in the Portal

Una vez en el portal podés:

| Acción | Descripción |
|---|---|
| 📊 **View usage** | Ver plan actual y estadísticas de uso |
| ⬆️ **Upgrade / Downgrade** | Cambiar tu suscripción |
| 💳 **Payment methods** | Actualizar métodos de pago e información de facturación |
| 🧾 **Invoices** | Descargar facturas e historial de facturación |
| 👥 **Manage members** | Gestionar miembros del equipo (planes de equipo) |
| ❌ **Cancel** | Cancelar tu suscripción si es necesario |

---

## Billing Practices

### Upgrading from Free tier (primera vez)

Si nunca antes actualizaste y upgradeas a mitad de mes:
- Se cobra un fee **prorrateado** por los días restantes
- Pero obtenés **acceso inmediato** al límite completo del nuevo plan

**Ejemplo:** Subscripción a Pro el 15 de abril → se cobra la mitad del fee mensual y se accede a todos los créditos del tier.

### Upgrading entre planes pagos

Si ya estás en un plan pago y subís a otro:
- Se cobra la diferencia de forma **retroactiva** para todo el mes
- Kiro recalcula el uso del mes bajo los límites del nuevo plan
- Esto puede evitar cargos de overage si ya superaste el límite anterior

### Downgrading

- Los downgrades tienen efecto al **inicio del siguiente mes**
- Los upgrades son **efectivos inmediatamente**
- Si bajás de Pro+ a Pro a mitad de mes, pagás el fee completo de Pro+ ese mes

### Overages

- Si superás el límite, las requests se pausan hasta que el límite se renueve al inicio del mes siguiente
- El Free tier tiene límites fijos y **no permite overage**
- En planes pagos podés habilitar overage para continuar trabajando sin interrupciones

---

## Need Help?

- Portal de soporte: [app.kiro.dev/account/usage?support_form](https://app.kiro.dev/account/usage?support_form)
- Email: [billing@kiro.dev](mailto:billing@kiro.dev)
- Chat de ayuda en el portal de suscripción