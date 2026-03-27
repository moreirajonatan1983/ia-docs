# Administrar su suscripción Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/billing/subscription-portal/](https://kiro.dev/docs/cli/billing/subscription-portal/)

---

## Accediendo al Portal de Suscripción

Accedé al portal en: **[app.kiro.dev/account/usage](https://app.kiro.dev/account/usage)**

Desde el CLI, use el comando `/usage` para ver el enlace al portal.

```
> /usage
```

---

## Qué puedes hacer en el portal

Una vez en el portal podés:

| Acción | Descripción |
|---|---|
| 📊 **Ver uso** | Ver plan actual y estadísticas de uso |
| ⬆️ **Actualizar / Degradar** | Cambiar tu suscripción |
| 💳 **Métodos de pago** | Actualizar métodos de pago e información de facturación |
| 🧾 **Facturas** | Descargar facturas e historial de facturación |
| 👥 **Administrar miembros** | Gestionar miembros del equipo (planes de equipo) |
| ❌ **Cancelar** | Cancelar tu suscripción si es necesario |

---

## Prácticas de facturación

### Actualización desde el nivel gratuito (primera vez)

Si nunca antes actualizaste y actualizaste a mitad de mes:
- Se cobra una tarifa **prorrateada** por los días restantes
- Pero obtenés **acceso inmediato** al límite completo del nuevo plan

**Ejemplo:** Subscripción a Pro el 15 de abril → se cobra la mitad del fee mensual y se accede a todos los créditos del tier.

### Actualizando entre aviones pagos

Si ya estás en un plan pago y subís a otro:
- Se cobra la diferencia de forma **retroactiva** para todo el mes
- Kiro recalcula el uso del mes bajo los límites del nuevo plan
- Esto puede evitar cargos de exceso si ya supera el límite anterior

### Degradación

- Los downgrades tienen efecto al **inicio del siguiente mes**
- Las actualizaciones son **efectivas inmediatamente**
- Si baja de Pro+ a Pro a mitad de mes, pagás el fee completo de Pro+ ese mes

### Excesos

- Si supera el límite, las solicitudes se pausan hasta que el límite se renueve al inicio del mes siguiente
- El nivel gratuito tiene límites fijos y **no permite exceso**
- En planos pagos podés habilitar overage para continuar trabajando sin interrupciones

---

## ¿Necesitas ayuda?

- Portal de soporte: [app.kiro.dev/account/usage?support_form](https://app.kiro.dev/account/usage?support_form)
- Correo electrónico: [billing@kiro.dev](mailto:billing@kiro.dev)
- Chat de ayuda en el portal de suscripción