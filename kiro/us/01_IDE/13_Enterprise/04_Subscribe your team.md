# Subscribe Your Team

> **Source:** [kiro.dev/docs/enterprise/subscribe/](https://kiro.dev/docs/enterprise/subscribe/)

---

## Prerequisites

Antes de comenzar, asegurate de tener:

- **Cuenta AWS** — [Crear cuenta →](https://docs.aws.amazon.com/accounts/latest/reference/manage-acct-creating.html)
- **Permisos AWS** — Como admin de Kiro, necesitás acceso a la Kiro console. Ver [permisos mínimos necesarios →](https://kiro.dev/docs/enterprise/iam/#policy-allow-administrators-to-configure-kiro-and-subscribe-users)
- **Identity Provider configurado** — IAM Identity Center, Okta o Microsoft Entra ID con los usuarios que querés suscribir
- **Usuarios y grupos** — Desde el directorio del IdP o de un IdP externo conectado a IAM Identity Center

---

## Create the Kiro Profile

![Subscribe Create Kiro Profile](https://kiro.dev/videos/docs/enterprise/subscribe-create-kiro-profile.mp4)

1. Iniciá sesión en la **AWS Management Console**
2. Cambiá a la **Kiro console**
3. Verificá que estás en la [región AWS soportada](https://kiro.dev/docs/enterprise/supported-regions) donde querés crear el Kiro profile
4. Elegí el botón **Sign up for Kiro**
5. Revisá el contenido del diálogo y elegí **Enable** — el Kiro profile se crea
6. (Opcional) Editá el profile con un nombre o descripción diferente desde la página de Settings

---

## Subscribe Your Team to Kiro

![Subscribe Add User](https://kiro.dev/videos/docs/enterprise/subscribe-add-user.mp4)

1. Cambiá a la **Kiro console**
2. Verificá que estás en la región AWS donde creaste el Kiro profile
3. En la página **Users & Groups**, elegí la pestaña **Users** o **Groups**
4. Elegí el botón **Add user** o **Add group** — aparece un diálogo para seleccionar el tier de suscripción
5. Elegí el tier deseado (Pro, Pro+, Power) y seleccioná **Continue**
6. En el search bar, buscá el grupo o usuario que querés suscribir
7. Los usuarios/grupos se autocompletan desde tu Identity Provider
8. Seleccioná y elegí **Assign** — los usuarios/grupos quedan suscriptos

---

## What Happens Next

- Los usuarios suscritos reciben un email dentro de las **24 horas** con instrucciones de descarga e inicio de sesión
- Podés gestionar suscripciones desde [Manage subscriptions →](./05_Manage%20subscriptions.md)