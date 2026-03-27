# Permisos de IAM

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/iam/](https://kiro.dev/docs/cli/privacy-and-security/iam/)

---

## Descripción general

Kiro CLI usa permisos IAM de AWS para autenticar y autorizar operaciones. Esta página describe los permisos requeridos para diferentes tipos de usuarios.

---

## Usuarios individuales (ID de constructor/Inicio de sesión social)

Para usuarios individuales que usan Builder ID, Okta o Google/GitHub:
- No se requieren permisos IAM de AWS
- La autenticación se realiza a través del portal de Kiro directamente

---

## Usuarios empresariales (Centro de identidad IAM)

Los usuarios de Enterprise pueden autenticarse con IAM Identity Center. Los administradores asignan permisos a través de la Consola Kiro.

### Permisos mínimos de usuario

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

## Permisos de administrador

Ver [Enterprise → IAM →](../14_Enterprise/10_IAM.md) para los permisos mínimos requeridos para administradores que configuran Kiro y suscriben usuarios.

---

## Integración de la CLI de AWS

Cuando usás las herramientas de AWS del CLI de Kiro, se usan las **credenciales AWS configuradas en tu entorno**:

```golpecito
# Kiro usa las credenciales AWS del sistema
exportar AWS_PROFILE=mi-perfil
exportar AWS_DEFAULT_REGION=us-east-1

# O credenciales directas
exportar AWS_ACCESS_KEY_ID=...
exportar AWS_SECRET_ACCESS_KEY=...
```

> Kiro nunca almacena las credenciales AWS — solo las lee del entorno en tiempo de ejecución.

---

## Principio de privilegio mínimo

**Mejores prácticas para el uso de Kiro con AWS:**

1. Usá **IAM roles con permisos mínimos** para las operaciones que Kiro puede realizar
2. Para testing, usamos cuentas AWS separadas de producción
3. Habilitá **MFA** en tu cuenta de AWS
4. Revise periódicamente qué comandos AWS está ejecutando Kiro mediante los **logs de auditoría**
5. En Enterprise, use la Kiro Console para controlar qué herramientas AWS pueden usar los usuarios

---

## Relacionado

- [IAM empresarial →](../14_Enterprise/10_IAM.md)
- [Consideraciones de seguridad →](../03_Chat/12_Consideraciones de seguridad.md)
- [Documentación de AWS IAM →](https://docs.aws.amazon.com/iam/latest/userguide/)