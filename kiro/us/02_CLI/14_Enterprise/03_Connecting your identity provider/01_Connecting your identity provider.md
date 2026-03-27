# Connecting Your Identity Provider

> **Source:** [kiro.dev/docs/cli/enterprise/identity-provider/](https://kiro.dev/docs/cli/enterprise/identity-provider/)

---

Kiro soporta conectar a tu Identity Provider externo directamente o a través de AWS IAM Identity Center.

---

## Supported Identity Sources

| Identity Source | Tipo |
|---|---|
| **AWS IAM Identity Center** | Nativo de AWS |
| **Okta** | IdP externo directo |
| **Microsoft Entra ID** | IdP externo directo |

---

## Option 1: AWS IAM Identity Center

Seguí las instrucciones en la [guía de IAM Identity Center →](https://kiro.dev/docs/cli/enterprise/identity-provider/iam-identity-center)

Pasos generales:
1. Habilitar IAM Identity Center en tu cuenta AWS
2. Agregar usuarios a tu directorio
3. Conectar IAM Identity Center a Kiro desde la Kiro Console

---

## Option 2: External Identity Provider (Direct)

### Okta

Seguí la [guía de configuración de Okta →](https://kiro.dev/docs/enterprise/identity-provider/okta)

Pasos generales:
1. Crear una aplicación Kiro en tu tenant de Okta
2. Configurar SAML/SCIM según las instrucciones
3. Conectar desde la Kiro Console

### Microsoft Entra ID (Azure AD)

Seguí la [guía de configuración de Microsoft Entra →](https://kiro.dev/docs/enterprise/identity-provider/microsoft-entra)

Pasos generales:
1. Registrar Kiro como Enterprise Application en Entra ID
2. Configurar SSO y provisioning
3. Conectar desde la Kiro Console

---

## Next Step

Una vez conectado el identity provider, podés suscribir esos usuarios o grupos a Kiro como se describe en la [guía de suscripción →](./04_Subscribe your team.md).