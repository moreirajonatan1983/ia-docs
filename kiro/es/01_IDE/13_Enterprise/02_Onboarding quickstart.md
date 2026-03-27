# Inicio rápido de incorporación

> **Fuente:** [kiro.dev/docs/enterprise/getting-started/](https://kiro.dev/docs/enterprise/getting-started/)

---

Esta guía está dirigida a **administradores** que quieren incorporar a su equipo en Kiro y gestionar sus suscripciones.

---

## Pasos para incorporar a su equipo

1. **Crear una cuenta AWS** (si no tienes una)
   - [Crear cuenta AWS →](https://docs.aws.amazon.com/accounts/latest/reference/manage-acct-creating.html)

2. **Sign in en AWS**
   - Como usuario root de AWS o usuario con rol privilegiado
   - Alternativamente, configurará un [administrador con permisos mínimos](https://kiro.dev/docs/enterprise/iam/#policy-allow-administrators-to-configure-kiro-and-subscribe-users)

3. **Conectar tu proveedor de identidad**
   - Agregue usuarios desde AWS IAM Identity Center, o conecte un IdP externo (Okta o Microsoft Entra ID)
   - [Guía de Proveedor de Identidad →](./03_Connecting%20your%20identity%20provider.md)

4. **Crear un perfil de Kiro y suscribir usuarios**
   - En la consola AWS, navegá a la **consola Kiro**
   - Crea un perfil y suscribete usuarios/grupos
   - [Guía de suscripción →](./04_Subscribe%20your%20team.md)

5. **Los usuarios recibirán un correo electrónico**
   - Dentro de las 24 horas, los usuarios suscritos reciben instrucciones de descarga e inicio de sesión para Kiro IDE y Kiro CLI.
   - Alternativamente pueden descargar desde [kiro.dev](https://kiro.dev/)