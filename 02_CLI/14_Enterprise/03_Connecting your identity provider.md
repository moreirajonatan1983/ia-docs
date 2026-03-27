# Conectando su proveedor de identidad

> **Fuente:** [kiro.dev/docs/cli/enterprise/identity-provider/](https://kiro.dev/docs/cli/enterprise/identity-provider/)

---

Kiro admite conectarse a su proveedor de identidad externo directamente o a través de AWS IAM Identity Center.

---

## Fuentes de identidad admitidas

| Fuente de identidad | Tipo |
|---|---|
| **Centro de identidad de AWS IAM** | Nativo de AWS |
| **Okta** | IdP externo directo |
| **ID de Microsoft Entra** | IdP externo directo |

---

## Opción 1: Centro de identidad de AWS IAM

Seguí las instrucciones en la [guía de IAM Identity Center →](https://kiro.dev/docs/cli/enterprise/identity-provider/iam-identity-center)

Pasos generales:
1. Habilitar IAM Identity Center en tu cuenta AWS
2. Agregar usuarios a tu directorio
3. Conectar IAM Identity Center a Kiro desde la Kiro Console

---

## Opción 2: Proveedor de identidad externo (directo)

### Okta

Seguí la [guía de configuración de Okta →](https://kiro.dev/docs/enterprise/identity-provider/okta)

Pasos generales:
1. Crea una aplicación Kiro en tu inquilino de Okta
2. Configurar SAML/SCIM según las instrucciones
3. Conectar desde la consola Kiro

### ID de Microsoft Entra (Azure AD)

Seguí la [guía de configuración de Microsoft Entra →](https://kiro.dev/docs/enterprise/identity-provider/microsoft-entra)

Pasos generales:
1. Registrador Kiro como Enterprise Application en Entra ID
2. Configurar SSO y aprovisionamiento
3. Conectar desde la consola Kiro

---

## Siguiente paso

Una vez conectado el proveedor de identidad, podrás suscribir a esos usuarios o grupos a Kiro como se describe en la [guía de suscripción →](./04_Subscribe your team.md).