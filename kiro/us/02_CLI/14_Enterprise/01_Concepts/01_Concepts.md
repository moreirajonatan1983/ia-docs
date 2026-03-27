# Concepts

> **Source:** [kiro.dev/docs/cli/enterprise/concepts/](https://kiro.dev/docs/cli/enterprise/concepts/)

---

Glosario de términos clave para administradores que gestionan suscripciones y usuarios de Kiro Enterprise.

---

## AWS IAM Identity Center

Servicio de AWS que provee un lugar centralizado para gestionar las identidades de los suscriptores de Kiro.

---

## AWS Region

Una ubicación física donde AWS agrupa sus data centers. Existen dos regiones relevantes para administradores de Kiro:

1. La región donde está habilitada tu instancia de IAM Identity Center (donde se gestionan identidades y se almacenan suscripciones)
2. La región donde se crea tu Kiro profile (donde se almacenan los datos — puede ser diferente)

Ver [Supported Regions →](./11_Supported regions.md) para más información.

---

## Group

Una colección de usuarios dentro de IAM Identity Center. Al suscribir un grupo a Kiro, los usuarios dentro de él se suscriben **individualmente** (no existe el concepto de suscripción grupal).

---

## Kiro Console

Una consola dentro de la AWS Console donde los admins crean y gestionan suscripciones de Kiro y controlan configuraciones. Aparece como **"Kiro"** en el dropdown de servicios de AWS.

---

## Kiro Credits

Unidad de consumo que mide el uso de las funcionalidades de AI de Kiro. Los créditos se gastan al interactuar con capacidades de AI y se reabastecen según el tier de suscripción.

---

## Kiro Enterprise User

Un usuario que fue agregado y suscrito a un tier de suscripción de Kiro a través de la AWS Console. Puede acceder a Kiro mediante IAM Identity Center, Okta o Microsoft Entra ID.

---

## Kiro Profile

La abstracción de gestión que define y aplica configuraciones administrativas y suscripciones a usuarios enterprise en una cuenta y región de AWS específicas.

Características:
- Corresponde a una combinación de cuenta AWS (management o member) + región
- Solo puede existir **un profile por cuenta AWS en una región dada**
- Se configura a través de la Kiro Console

---

## Kiro Subscription Tier

Un plan de pricing específico con un número predeterminado de Kiro credits.

---

## Summary Table

| Concepto | Descripción breve |
|---|---|
| **IAM Identity Center** | Gestión centralizada de identidades |
| **AWS Region** | Ubicación física de los data centers |
| **Group** | Colección de usuarios (suscripción individual) |
| **Kiro Console** | UI en AWS Console para gestionar Kiro |
| **Kiro Credits** | Unidad de consumo de AI |
| **Enterprise User** | Usuario suscrito vía AWS Console |
| **Kiro Profile** | Abstracción de gestión por cuenta + región |
| **Subscription Tier** | Plan de pricing con créditos predeterminados |