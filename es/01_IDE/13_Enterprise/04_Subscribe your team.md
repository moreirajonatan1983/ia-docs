# Suscríbete a tu equipo

> **Fuente:** [kiro.dev/docs/enterprise/subscribe/](https://kiro.dev/docs/enterprise/subscribe/)

---

## Requisitos previos

Antes de comenzar, asegúrese de tener:

- **Cuenta AWS** — [Crear cuenta →](https://docs.aws.amazon.com/accounts/latest/reference/manage-acct-creating.html)
- **Permisos AWS** — Como administrador de Kiro, necesitas acceder a la consola de Kiro. Ver [permisos mínimos necesarios →](https://kiro.dev/docs/enterprise/iam/#policy-allow-administrators-to-configure-kiro-and-subscribe-users)
- **Proveedor de identidad configurado** — IAM Identity Center, Okta o Microsoft Entra ID con los usuarios que quieren suscribirse
- **Usuarios y grupos** — Desde el directorio del IdP o de un IdP externo conectado a IAM Identity Center

---

## Crea el perfil de Kiro

![Suscribirse Crear perfil de Kiro](https://kiro.dev/videos/docs/enterprise/subscribe-create-kiro-profile.mp4)

1. Iniciá sesión en la **AWS Management Console**
2. Cambiá a la **consola Kiro**
3. Verifica que estás en la [región AWS soportada](https://kiro.dev/docs/enterprise/supported-regions) donde quieres crear el perfil de Kiro
4. Elegí el botón **Regístrese en Kiro**
5. Revisá el contenido del diálogo y elige **Enable** — el perfil de Kiro se crea
6. (Opcional) Edite el perfil con un nombre o descripción diferente desde la página de Configuración

---

## Suscríbete a tu equipo a Kiro

![Suscribirse Agregar usuario](https://kiro.dev/videos/docs/enterprise/subscribe-add-user.mp4)

1. Cambiá a la **consola Kiro**
2. Verifica que estás en la región AWS donde creaste el perfil de Kiro
3. En la página **Usuarios y Grupos**, elija la pestaña **Usuarios** o **Grupos**
4. Elija el botón **Agregar usuario** o **Agregar grupo** — aparece un diálogo para seleccionar el nivel de suscripción
5. Elija el nivel deseado (Pro, Pro+, Power) y seleccione **Continuar**
6. En la barra de búsqueda, busca el grupo o usuario que querrás suscribirse
7. Los usuarios/grupos se autocompletan desde tu Identity Provider
8. Seleccioná y elegí **Assign** — los usuarios/grupos quedan suscriptos

---

## ¿Qué pasa después?

- Los usuarios suscritos reciben un correo electrónico dentro de las **24 horas** con instrucciones de descarga e inicio de sesión
- Podés gestionar suscripciones desde [Gestionar suscripciones →](./05_Manage%20subscriptions.md)