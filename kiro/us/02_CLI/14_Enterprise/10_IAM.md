# IAM

> **Source:** [kiro.dev/docs/cli/enterprise/iam/](https://kiro.dev/docs/cli/enterprise/iam/)

---

## IAM Permissions for Enterprise Admins

Los administradores de Kiro Enterprise necesitan permisos IAM específicos para gestionar la plataforma desde la AWS Console.

---

## Policy: Allow Administrators to Configure Kiro and Subscribe Users

Para que los administradores puedan configurar Kiro y suscribir usuarios **sin permisos de root**, podés asignarles una política IAM con permisos mínimos:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "kiro:*",
        "sso:ListInstances",
        "sso:ListPermissionSets",
        "identitystore:ListUsers",
        "identitystore:ListGroups",
        "identitystore:DescribeUser",
        "identitystore:DescribeGroup"
      ],
      "Resource": "*"
    }
  ]
}
```

---

## Required Permissions Summary

| Permiso | Descripción |
|---|---|
| `kiro:*` | Acceso completo a Kiro Console |
| `sso:ListInstances` | Listar instancias de IAM Identity Center |
| `sso:ListPermissionSets` | Ver permission sets de SSO |
| `identitystore:ListUsers` | Listar usuarios en el directorio |
| `identitystore:ListGroups` | Listar grupos en el directorio |
| `identitystore:DescribeUser` | Ver detalles de usuarios |
| `identitystore:DescribeGroup` | Ver detalles de grupos |

---

## Signing In

Podés iniciar sesión en la AWS Console como:
- **AWS root user** (no recomendado para uso cotidiano)
- **Usuario con rol privilegiado** (recomendado)
- **Usuario con permisos mínimos** según la política de arriba

---

## Related

- [Onboarding quickstart →](./02_Onboarding quickstart.md)
- [Connecting your identity provider →](./03_Connecting your identity provider.md)
- [IAM Identity Center docs →](https://kiro.dev/docs/cli/enterprise/identity-provider/iam-identity-center)