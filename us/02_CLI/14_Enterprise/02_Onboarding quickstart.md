# Onboarding Quickstart

> **Source:** [kiro.dev/docs/cli/enterprise/getting-started/](https://kiro.dev/docs/cli/enterprise/getting-started/)

---

## Audience

Esta guía está dirigida a **administradores** que desean incorporar su equipo a Kiro y gestionar sus suscripciones.

---

## To Onboard Your Team to Kiro

### Paso 1 — Crear una cuenta AWS

Si no tenés una, [creá una cuenta AWS](https://docs.aws.amazon.com/accounts/latest/reference/manage-acct-creating.html).

### Paso 2 — Iniciar sesión en AWS

Podés iniciar como:
- AWS root user
- Usuario con un rol privilegiado
- O [configurar permisos mínimos para administradores](https://kiro.dev/docs/cli/enterprise/iam/#policy-allow-administrators-to-configure-kiro-and-subscribe-users)

### Paso 3 — Conectar tu Identity Provider

Conectar a tu proveedor de identidad. Podés:
- Agregar usuarios directamente desde **AWS IAM Identity Center**
- Conectar a un IdP externo: **Okta** o **Microsoft Entra ID**

Ver [Connecting your identity provider →](./03_Connecting your identity provider.md) para instrucciones detalladas.

### Paso 4 — Crear un Kiro Profile y suscribir usuarios

Dentro de la AWS Console:
1. Navegar a la **Kiro Console**
2. Usar la UI disponible para crear un profile
3. El profile conecta las identidades de usuario con sus suscripciones y configuraciones de Kiro
4. Una vez creado, importar usuarios y grupos
5. [Suscribir el equipo a Kiro](https://kiro.dev/docs/cli/enterprise/subscribe)

> Solo puede existir **un profile por cuenta AWS en una región dada**.

### Paso 5 — Los usuarios verifican su email

Dentro de las **24 horas** de ser suscritos, los usuarios recibirán un email con:
- Instrucciones de descarga para Kiro IDE y Kiro CLI
- Instrucciones de inicio de sesión

Alternativamente, pueden descargar Kiro desde [kiro.dev](https://kiro.dev/).

---

## Quick Reference

```
Admin → AWS Console → Kiro Console → Crear Profile 
      → Importar usuarios/grupos → Suscribir al plan
      
Usuario ← Email con instrucciones ← Kiro backend
```