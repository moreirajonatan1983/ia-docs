# Inicio rápido de incorporación

> **Fuente:** [kiro.dev/docs/cli/enterprise/getting-started/](https://kiro.dev/docs/cli/enterprise/getting-started/)

---

## Audiencia

Esta guía está dirigida a **administradores** que desean incorporar su equipo a Kiro y gestionar sus suscripciones.

---

## Para incorporar tu equipo a Kiro

### Paso 1 — Crear una cuenta AWS

Si no tienes una, [creá una cuenta AWS](https://docs.aws.amazon.com/accounts/latest/reference/manage-acct-creating.html).

### Paso 2 — Iniciar sesión en AWS

Podés iniciar como:
- Usuario raíz de AWS
- Usuario con un rol privilegiado
- O [configurar permisos mínimos para administradores](https://kiro.dev/docs/cli/enterprise/iam/#policy-allow-administrators-to-configure-kiro-and-subscribe-users)

### Paso 3 — Conectar tu proveedor de identidad

Conectar a tu proveedor de identidad. Podés:
- Agregar usuarios directamente desde **AWS IAM Identity Center**
- Conectar a un IdP externo: **Okta** o **Microsoft Entra ID**

Ver [Conectando tu proveedor de identidad →](./03_Conectando tu proveedor de identidad.md) para instrucciones detalladas.

### Paso 4 — Crear un perfil de Kiro y suscribir usuarios

Dentro de la consola de AWS:
1. Navegar a la **Consola Kiro**
2. Usar la UI disponible para crear un perfil
3. El perfil conecta las identidades de usuario con sus suscripciones y configuraciones de Kiro
4. Una vez creado, importa usuarios y grupos
5. [Suscribir el equipo a Kiro](https://kiro.dev/docs/cli/enterprise/subscribe)

> Solo puede existir **un perfil por cuenta AWS en una región dada**.

### Paso 5 — Los usuarios verifican su correo electrónico

Dentro de las **24 horas** de ser suscritos, los usuarios recibirán un correo electrónico con:
- Instrucciones de descarga para Kiro IDE y Kiro CLI
- Instrucciones de inicio de sesión

Alternativamente, pueden descargar Kiro desde [kiro.dev](https://kiro.dev/).

---

## Referencia rápida

```
Admin → AWS Console → Kiro Console → Crear Profile 
      → Importar usuarios/grupos → Suscribir al plan
      
Usuario ← Email con instrucciones ← Kiro backend
```