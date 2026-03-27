# Conectando su proveedor de identidad

> **Fuente:** [kiro.dev/docs/enterprise/identity-provider/](https://kiro.dev/docs/enterprise/identity-provider/)

---

Kiro soporta conectar su proveedor de identidad directamente o a través de AWS IAM Identity Center.

---

## Fuentes de identidad admitidas

| Opción | Descripción |
|---|---|
| **Centro de identidad de AWS IAM** | Gestión de identidades centralizadas directamente en AWS |
| **Okta** (IdP directo) | Conecta Okta directamente a Kiro |
| **ID de Microsoft Entra** (IDP directo) | Conecte Microsoft Entra ID directamente a Kiro |

---

## Opción 1: Centro de identidad de AWS IAM

Consultor [guía de IAM Identity Center →](https://kiro.dev/docs/enterprise/identity-provider/iam-identity-center)

> **Recomendación:** Utilice AWS Organizations al configurar IAM Identity Center para habilitar una instancia de organización con gestión centralizada de identidades en múltiples cuentas AWS.
> ⚠️ Las instancias de cuenta individual **no pueden** actualizarse a instancias de organización — requieren eliminación y recreación.

---

## Opción 2: Proveedor de identidad externo (directo)

### Okta
Consultar [guía de configuración de Okta →](https://kiro.dev/docs/enterprise/identity-provider/okta)

### Identificación de Microsoft Entra
Consultar [Guía de configuración de Microsoft Entra ID →](https://kiro.dev/docs/enterprise/identity-provider/microsoft-entra)

---

## Próximos pasos

Una vez conectado el proveedor de identidad, podrás suscribir usuarios esos o grupos a Kiro:
- [Suscribe tu equipo →](./04_Subscribe%20your%20team.md)