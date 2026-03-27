# Administrar suscripciones

> **Fuente:** [kiro.dev/docs/enterprise/subscription-management/](https://kiro.dev/docs/enterprise/subscription-management/)

---

## Cambiar los planes de suscripción de Kiro

![Administrar suscripción Cambiar suscripción](https://kiro.dev/videos/docs/enterprise/manage-subscription-change-subscription.mp4)

1. Iniciá sesión en la **AWS Management Console**
2. Cambiá a la **consola Kiro**
3. En la página **Usuarios y Grupos**, elija la pestaña correspondiente
4. Seleccioná el usuario o grupo cuya suscripción quiera cambiar
5. Elegí **Change plan** y seleccioná el nuevo plan → **Continuar**

> - **Actualizaciones:** Efectivos de forma inmediata
> - **Downgrades:** Efectivos al inicio del mes siguiente

---

## Darse de baja de usuarios de Kiro

![Administrar suscripción Desactivar usuario](https://kiro.dev/videos/docs/enterprise/manage-subscription-deactivate-user.mp4)

1. En la **consola Kiro**, ve a **Usuarios y Grupos**
2. Selecciona el usuario o grupo a desuscribir
3. Elegí **Desactivar plan** → revisá el diálogo y elegí **Cancelar suscripción**

Los usuarios desuscriptos pierden acceso **de manera inmediata** a las características pagas de Kiro.

---

## Habilitar excedentes para usuarios de Kiro

Los excedentes permiten a los usuarios continuar trabajando para superar los límites de su plan. Por defecto están **deshabilitados**. Al habilitarse, aplique a **todos los usuarios del perfil**.

1. En la **consola Kiro**, elige **Configuración**
2. Busca la sección **Kiro settings**
3. Activá **Excedentes**

> ℹ️ La configuración de gorras personalizadas para excedentes no está disponible aún (próximamente).

---

## Estados de suscripción

| Estado | Descripción |
|---|---|
| **Activo** | El usuario está suscripto. Se te cobra por la suscripción |
| **Cancelado** | Suscripción cancelada por un administrador. Sin acceso a características pagas |
| **Pendiente** | Suscripto pero no activó la suscripción. No se cobra; sin datos en la columna "Último activo" |

> Los grupos no tienen estados propios — las suscripciones se asignan a usuarios individuales.