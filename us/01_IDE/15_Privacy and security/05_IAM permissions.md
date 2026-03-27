# IAM Permissions

> **Source:** [kiro.dev/docs/privacy-and-security/iam-permissions/](https://kiro.dev/docs/privacy-and-security/iam-permissions/)

---

Para crear un Kiro profile y gestionar suscripciones, el rol que administra Kiro necesita los siguientes permisos IAM en la cuenta AWS.

---

## General Permissions

Requeridos independientemente del identity store utilizado:

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

## External Identity Provider Permissions

Si conectás un identity provider externo (Okta, Microsoft Entra ID), también necesitás:

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

## Additional Resources

| Recurso | URL |
|---|---|
| AWS IAM Documentation | [docs.aws.amazon.com/iam/](https://docs.aws.amazon.com/iam/) |
| IAM Best Practices | [IAM Best Practices Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) |
| Kiro Data Protection | [Data protection →](./01_Data%20protection.md) |
| Kiro Infrastructure Security | [Infrastructure security →](./04_Infrastructure%20security.md) |
| Enterprise IAM Policy (completa) | [Enterprise IAM →](../13_Enterprise/10_IAM.md) |