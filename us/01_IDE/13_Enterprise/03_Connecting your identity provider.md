# Connecting Your Identity Provider

> **Source:** [kiro.dev/docs/enterprise/identity-provider/](https://kiro.dev/docs/enterprise/identity-provider/)

---

Kiro soporta conectar tu Identity Provider directamente o a través de AWS IAM Identity Center.

---

## Supported Identity Sources

| Opción | Descripción |
|---|---|
| **AWS IAM Identity Center** | Gestión de identidades centralizadas directamente en AWS |
| **Okta** (Direct IdP) | Conectá Okta directamente a Kiro |
| **Microsoft Entra ID** (Direct IdP) | Conectá Microsoft Entra ID directamente a Kiro |

---

## Option 1: AWS IAM Identity Center

Consultar [IAM Identity Center guide →](https://kiro.dev/docs/enterprise/identity-provider/iam-identity-center)

> **Recomendación:** Usá AWS Organizations al configurar IAM Identity Center para habilitar una instancia de organización con gestión centralizada de identidades en múltiples cuentas AWS.
> ⚠️ Las instancias de cuenta individual **no pueden** upgradearse a instancias de organización — requieren eliminación y recreación.

---

## Option 2: External Identity Provider (Direct)

### Okta
Consultar [Okta setup guide →](https://kiro.dev/docs/enterprise/identity-provider/okta)

### Microsoft Entra ID
Consultar [Microsoft Entra ID setup guide →](https://kiro.dev/docs/enterprise/identity-provider/microsoft-entra)

---

## Next Steps

Una vez conectado el identity provider, podés suscribir esos usuarios o grupos a Kiro:
- [Subscribe your team →](./04_Subscribe%20your%20team.md)