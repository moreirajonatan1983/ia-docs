# Managing Usage Notifications

> **Source:** [kiro.dev/docs/billing/proactive-usage-notifications/](https://kiro.dev/docs/billing/proactive-usage-notifications/)

---

Kiro envía notificaciones proactivas para mantenerte informado sobre tu consumo de créditos.

---

## Notification Types

### Low Resource Notifications

Al alcanzar el **80% del uso mensual de créditos**, Kiro envía una notificación:

| Situación | Notificación |
|---|---|
| **Free tier** | Sugerencia para upgradear; recordatorio de que los créditos resetean mensualmente y no hay overages |
| **Paid (puede upgradear)** | Opción de upgradear para más créditos o habilitar overages |
| **Paid (tier máximo)** | Opción de habilitar overages para acceso ininterrumpido |

### Overage Notifications

Al superar el límite mensual con overages habilitados:
- Si puede upgradear: se te propone upgradear o ver la tasa de overages
- Si ya está en el tier máximo: alerta de que los overages están activos y cuándo resetea el límite

### Usage Reset Notifications

Al inicio de cada ciclo de facturación:
- **Sin overages:** Alerta con la cantidad de créditos disponibles
- **Con overages:** Alerta de créditos disponibles + confirmación de overages activos

---

## Managing Notification Preferences

Las notificaciones de facturación están habilitadas por defecto. Para deshabilitarlas:

1. `Cmd/Ctrl + Shift + P` → **Command Palette**
2. Buscá **Notifications: Billing**
3. Desmarcá la opción para deshabilitar notificaciones de facturación

---

## Understanding Your Usage Patterns

Las notificaciones proactivas te ayudan a:

- **Identificar picos de uso** — Entender cuándo y por qué aumenta tu consumo
- **Elegir el plan correcto** — Determinar si necesitás upgradear o downgrade
- **Optimizar workflows** — Ajustar patrones de desarrollo para usar créditos eficientemente
- **Evitar sorpresas** — Estar informado sobre posibles cargos de overage antes de que ocurran

> 💡 Si recibís alertas de 80% de uso temprano en tu ciclo de facturación, considerá upgradear a un tier superior.