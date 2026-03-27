# SOY

> **Fuente:** [kiro.dev/docs/cli/enterprise/iam/](https://kiro.dev/docs/cli/enterprise/iam/)

---

## Permisos de IAM para administradores empresariales

Los administradores de Kiro Enterprise necesitan permisos específicos de IAM para gestionar la plataforma desde la consola AWS.

---

## Política: Permitir a los administradores configurar Kiro y suscribir usuarios

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

## Resumen de permisos requeridos

| permiso | Descripción |
|---|---|
| `kiro:*` | Acceso completo a la consola Kiro |
| `sso:ListInstances` | Listar instancias de IAM Identity Center |
| `sso:ListPermissionSets` | Ver conjuntos de permisos de SSO |
| `almacén de identidades:ListUsers` | Listar usuarios en el directorio |
| `almacén de identidades:ListGroups` | Listar grupos en el directorio |
| `identitystore:DescribeUser` | Ver detalles de usuarios |
| `almacén de identidad:DescribeGroup` | Ver detalles de grupos |

---

## Iniciar sesión

Podés iniciar sesión en la consola AWS como:
- **Usuario root de AWS** (no recomendado para uso cotidiano)
- **Usuario con rol privilegiado** (recomendado)
- **Usuario con permisos mínimos** según la política de arriba

---

## Relacionado

- [Inicio rápido de incorporación →](./02_Inicio rápido de incorporación.md)
- [Conectando tu proveedor de identidad →](./03_Conectando tu proveedor de identidad.md)
- [Documentos del Centro de identidad de IAM →](https://kiro.dev/docs/cli/enterprise/identity-provider/iam-identity-center)