# IAM: gestión de identidad y acceso

> **Fuente:** [kiro.dev/docs/enterprise/iam/](https://kiro.dev/docs/enterprise/iam/)

---

## Políticas basadas en la identidad para Kiro

Para que un administrador pueda gestionar Kiro desde la consola de AWS (suscribir usuarios, configurar la integración con IAM Identity Center y AWS Organizations, gestionar la configuración), necesita la siguiente política IAM mínima:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "sso:ListInstances", "sso:CreateInstance", "sso:CreateApplication",
        "sso:PutApplicationAuthenticationMethod", "sso:PutApplicationGrant",
        "sso:ListApplications", "sso:DescribeInstance", "sso:DescribeApplication",
        "sso:DeleteApplication", "sso:CreateApplicationAssignment",
        "sso:DeleteApplicationAssignment", "sso:UpdateApplication",
        "sso:DescribeRegisteredRegions", "sso:GetSSOStatus"
      ],
      "Resource": ["*"]
    },
    {
      "Effect": "Allow",
      "Action": [
        "user-subscriptions:ListClaims", "user-subscriptions:CreateClaim",
        "user-subscriptions:DeleteClaim", "user-subscriptions:UpdateClaim",
        "user-subscriptions:SetOverageConfig"
      ],
      "Resource": ["*"]
    },
    {
      "Effect": "Allow",
      "Action": [
        "codewhisperer:UpdateProfile", "codewhisperer:ListProfiles",
        "codewhisperer:CreateProfile"
      ],
      "Resource": ["*"]
    },
    {
      "Effect": "Allow",
      "Action": ["q:ListDashboardMetrics", "q:CreateAssignment", "q:DeleteAssignment"],
      "Resource": ["*"]
    },
    {
      "Effect": "Allow",
      "Action": ["cloudwatch:GetMetricData", "cloudwatch:ListMetrics"],
      "Resource": ["*"]
    }
  ]
}
```

> La política completa también incluye permisos para `iam`, `identitystore`, `sso-directory`, `organizations`, `kms` y `signin`. Ver [documentación completa →](https://kiro.dev/docs/enterprise/iam/#policy-allow-administrators-to-configure-kiro-and-subscribe-users)

---

## Roles vinculados al servicio

Kiro usa los siguientes roles vinculados a servicios de AWS:

| papel | Propósito |
|---|---|
| `AWSServiceRoleForUserSubscriptions` | Gestión de suscripciones de usuarios |
| `AWSServiceRoleForAmazonQDeveloper` | Integración con Amazon Q Developer |