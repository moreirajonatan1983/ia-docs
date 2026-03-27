# Permisos de IAM

> **Fuente:** [kiro.dev/docs/privacy-and-security/iam-permissions/](https://kiro.dev/docs/privacy-and-security/iam-permissions/)

---

Para crear un perfil de Kiro y gestionar suscripciones, el rol que administra Kiro necesita los siguientes permisos IAM en la cuenta AWS.

---

## Permisos generales

Requeridos independientemente del almacén de identidad utilizado:

```
codewhisperer:ListProfiles
codewhisperer:CreateProfile
codewhisperer:DeleteProfile
codewhisperer:UpdateProfile
codewhisperer:TagResource
codewhisperer:UntagResource
codewhisperer:ListTagsForResource
codewhisperer:AllowVendedLogDeliveryForResource
q:ListDashboardMetrics
```

---

## Permisos de proveedores de identidad externos

Si conectas un proveedor de identidad externo (Okta, Microsoft Entra ID), también necesitarás:

```
q:ListLoginDomains
q:AssociateLoginDomain
q:DisassociateLoginDomain
q:ListScimAccessTokens
q:CreateScimAccessToken
q:DeleteScimAccessToken
q:ListGroups
q:ListUsers
q:BatchDescribeUsers
q:BatchDescribeGroups
```

---

## Recursos adicionales

| Recurso | URL |
|---|---|
| Documentación de AWS IAM | [docs.aws.amazon.com/iam/](https://docs.aws.amazon.com/iam/) |
| Mejores prácticas de IAM | [Guía de mejores prácticas de IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) |
| Protección de datos Kiro | [Protección de datos →](./01_Data%20protection.md) |
| Seguridad de infraestructura Kiro | [Seguridad de infraestructura →](./04_Infrastructure%20security.md) |
| Política de IAM empresarial (completa) | [IAM empresarial →](../13_Enterprise/10_IAM.md) |