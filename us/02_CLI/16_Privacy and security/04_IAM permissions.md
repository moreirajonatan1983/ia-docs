# IAM Permissions

> **Source:** [kiro.dev/docs/cli/privacy-and-security/iam/](https://kiro.dev/docs/cli/privacy-and-security/iam/)

---

## Overview

Kiro CLI usa permisos IAM de AWS para autenticar y autorizar operaciones. Esta página describe los permisos requeridos para diferentes tipos de usuarios.

---

## Individual Users (Builder ID / Social Login)

Para usuarios individuales que usan Builder ID, Okta o Google/GitHub:
- No se requieren permisos IAM de AWS
- La autenticación se realiza a través del portal de Kiro directamente

---

## Enterprise Users (IAM Identity Center)

Los usuarios Enterprise autentican con IAM Identity Center. Los administradores asignan permisos a través de la Kiro Console.

### Minimum User Permissions

Para que un usuario pueda usar Kiro CLI con Identity Center:

```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": [
      "kiro:SendMessage",
      "kiro:GetSession",
      "kiro:StartSession"
    ],
    "Resource": "*"
  }]
}
```

---

## Administrator Permissions

Ver [Enterprise → IAM →](../14_Enterprise/10_IAM.md) para los permisos mínimos requeridos para administradores que configuran Kiro y suscriben usuarios.

---

## AWS CLI Integration

Cuando usás las tools de AWS del CLI de Kiro, se usan las **credenciales AWS configuradas en tu entorno**:

```bash
# Kiro usa las credenciales AWS del sistema
export AWS_PROFILE=my-profile
export AWS_DEFAULT_REGION=us-east-1

# O credenciales directas
export AWS_ACCESS_KEY_ID=...
export AWS_SECRET_ACCESS_KEY=...
```

> Kiro nunca almacena las credenciales AWS — solo las lee del entorno en tiempo de ejecución.

---

## Principle of Least Privilege

**Best practices para el uso de Kiro con AWS:**

1. Usá **IAM roles con permisos mínimos** para las operaciones que Kiro puede realizar
2. Para testing, usá cuentas AWS separadas de producción
3. Habilitá **MFA** en tu AWS account
4. Revisá regularmente qué comandos AWS está ejecutando Kiro mediante los **logs de auditoría**
5. En Enterprise, usá el Kiro Console para controlar qué tools AWS pueden usar los usuarios

---

## Related

- [Enterprise IAM →](../14_Enterprise/10_IAM.md)
- [Security considerations →](../03_Chat/12_Security considerations.md)
- [AWS IAM documentation →](https://docs.aws.amazon.com/iam/latest/userguide/)