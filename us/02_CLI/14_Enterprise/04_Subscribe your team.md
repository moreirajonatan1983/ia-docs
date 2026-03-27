# Subscribe Your Team

> **Source:** [kiro.dev/docs/cli/enterprise/subscribe/](https://kiro.dev/docs/cli/enterprise/subscribe/)

---

Una vez que tu identity provider está conectado y tu Kiro profile está creado, podés suscribir usuarios o grupos a Kiro desde la Kiro Console.

---

## Subscribing Users

1. Iniciar sesión en **AWS Management Console**
2. Navegar a la **Kiro Console** (si no la ves, verificá que estás en la AWS Region correcta)
3. Ir a **Users & Groups → Users tab**
4. Seleccionar el usuario a suscribir
5. Elegir el plan de suscripción
6. Confirmar

## Subscribing Groups

1. Repetir los pasos 1-3 anteriores
2. Ir al **Groups tab**
3. Seleccionar el grupo
4. Elegir el plan de suscripción y confirmar

> Al suscribir un grupo, **cada usuario dentro del grupo** se suscribe individualmente. No existe suscripción grupal como unidad de cobro.

---

## After Subscribing

Dentro de las **24 horas**, los usuarios suscritos recibirán un email con:
- Instrucciones de descarga para Kiro IDE y Kiro CLI
- Instrucciones de inicio de sesión con su identity provider

---

## Subscription Statuses

| Estado | Descripción |
|---|---|
| **Active** | El usuario está suscrito a Kiro. Se le cobra. |
| **Canceled** | La suscripción fue cancelada por un administrador. Sin acceso a features pagas. |
| **Pending** | Suscrito pero no ha activado aún su suscripción. No se cobra. |

Los estados se visualizan en la página **Subscriptions** de la Kiro Console (solo en el tab Users, no en Groups).