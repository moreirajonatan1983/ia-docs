# Enterprise Concepts

> **Source:** [kiro.dev/docs/enterprise/concepts/](https://kiro.dev/docs/enterprise/concepts/)

---

Glosario de términos clave para administradores que gestionan suscripciones y usuarios de Kiro Enterprise.

---

## Concepts Reference

| Término | Definición |
|---|---|
| **AWS IAM Identity Center** | Servicio AWS que provee un lugar central para gestionar las identidades de usuarios de Kiro |
| **AWS Region** | Ubicación física donde AWS agrupa sus data centers. Relevante en dos dimensiones: (1) región donde está habilitado IAM Identity Center, y (2) región donde se crea el Kiro profile (donde se almacenan los datos) |
| **Group** | Colección de usuarios dentro de IAM Identity Center. Al suscribir un grupo a Kiro, los usuarios individuales se suscriben por separado (no existe concepto de suscripción grupal) |
| **Kiro console** | Consola dentro de la AWS console donde creás y gestionás suscripciones Kiro y configurás settings. Aparece como "Kiro" en el dropdown de servicios AWS |
| **Kiro credits** | Unidad de consumo que mide el uso de las features de IA de Kiro. Se gastan en interacciones con IA y se reponen según el tier de suscripción |
| **Kiro enterprise user** | Usuario que fue agregado y suscripto a un tier de Kiro a través de la AWS console, con acceso mediante IAM Identity Center, Okta o Microsoft Entra ID |
| **Kiro profile** | Abstracción de gestión que define y aplica settings administrativos y suscripciones a usuarios enterprise en una cuenta AWS y región determinadas. Una cuenta AWS + región = un único profile. Se configura desde la Kiro console |
| **Kiro subscription tier** | Plan de precios con una cantidad predeterminada de créditos Kiro (Free, Pro, Pro+, Power) |