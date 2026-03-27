# Onboarding Quickstart

> **Source:** [kiro.dev/docs/enterprise/getting-started/](https://kiro.dev/docs/enterprise/getting-started/)

---

Esta guía está dirigida a **administradores** que quieren incorporar a su equipo en Kiro y gestionar sus suscripciones.

---

## Steps to Onboard Your Team

1. **Crear una cuenta AWS** (si no tenés una)
   - [Crear cuenta AWS →](https://docs.aws.amazon.com/accounts/latest/reference/manage-acct-creating.html)

2. **Iniciar sesión en AWS**
   - Como AWS root user o usuario con rol privilegiado
   - Alternativamente, configurá un [administrador con permisos mínimos](https://kiro.dev/docs/enterprise/iam/#policy-allow-administrators-to-configure-kiro-and-subscribe-users)

3. **Conectar tu Identity Provider**
   - Agregá usuarios desde AWS IAM Identity Center, o conectá un IdP externo (Okta o Microsoft Entra ID)
   - [Guía de Identity Provider →](./03_Connecting%20your%20identity%20provider.md)

4. **Crear un Kiro profile y suscribir usuarios**
   - En la AWS console, navegá a la **Kiro console**
   - Creá un profile y suscribí users/groups
   - [Guía de suscripción →](./04_Subscribe%20your%20team.md)

5. **Los usuarios recibirán un email**
   - Dentro de las 24 horas, los usuarios suscritos reciben instrucciones de descarga e inicio de sesión para Kiro IDE y Kiro CLI
   - Alternativamente pueden descargar desde [kiro.dev](https://kiro.dev/)