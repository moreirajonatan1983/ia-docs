# Suscríbete a tu equipo

> **Fuente:** [kiro.dev/docs/cli/enterprise/subscribe/](https://kiro.dev/docs/cli/enterprise/subscribe/)

---

Una vez que tu proveedor de identidad esté conectado y tu perfil de Kiro esté creado, podrás suscribir usuarios o grupos a Kiro desde la Kiro Console.

---

## Usuarios suscritos

1. Sign in en **AWS Management Console**
2. Navegar a la **Kiro Console** (si no la ves, verifica que estás en la región AWS correcta)
3. Navegá a **Usuarios y grupos → pestaña Usuarios**
4. Seleccionar el usuario a suscribir
5. Elegir el plan de suscripción
6. Confirmar

## Grupos de suscripción

1. Repetir los pasos 1-3 anteriores
2. Ir al **Pestaña Grupos**
3. Seleccionar el grupo
4. Elegir el plan de suscripción y confirmar

> Al suscribir un grupo, **cada usuario dentro del grupo** se suscribe individualmente. No existe suscripción grupal como unidad de cobro.

---

## Después de suscribirse

Dentro de las **24 horas**, los usuarios suscritos recibirán un correo electrónico con:
- Instrucciones de descarga para Kiro IDE y Kiro CLI
- Instrucciones de inicio de sesión con su proveedor de identidad

---

## Estados de suscripción

| Estado | Descripción |
|---|---|
| **Activo** | El usuario está suscrito a Kiro. Se le cobra. |
| **Cancelado** | La suscripción fue cancelada por un administrador. Sin acceso a características pagas. |
| **Pendiente** | Suscrito pero no ha activado aún su suscripción. No se cobra. |

Los estados se visualizan en la página **Suscripciones** de la Kiro Console (solo en la pestaña Usuarios, no en Grupos).