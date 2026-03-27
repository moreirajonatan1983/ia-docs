# Monitorear y rastrear

> **Fuente:** [kiro.dev/docs/cli/enterprise/](https://kiro.dev/docs/cli/enterprise/) | [kiro.dev/docs/cli/enterprise/settings/](https://kiro.dev/docs/cli/enterprise/settings/)

---

Kiro Enterprise proporciona herramientas para que los administradores monitoreen y rastreen el uso de la plataforma.

---

## Panel de uso

Visualice el uso de Kiro a nivel de organización desde la **Kiro Console**:

- Créditos consumidos por período
- Usuarios activos
- Distribución de uso por nivel

**Cómo acceder:**
1. Iniciar sesión en la **AWS Management Console**
2. Navegar a la **Consola Kiro**
3. Ver la sección de **Uso/Panel**

---

## Actividad por usuario

Visualice la actividad individual de los usuarios:
- Última actividad por usuario (columna `Última activa` en la página de Suscripciones)
- Usuarios con estado **Pending** no tendrán datos en esta columna (no han activado su suscripción)

---

## Registro rápido

Los administradores pueden habilitar el registro de mensajes de los usuarios para auditoría y cumplimiento.

**Para habilitar:**
1. Abrir la **Consola Kiro**
2. Vaya a **Configuración**
3. Activar **Registro rápido**

Ver [Registrar mensajes de usuario →](https://kiro.dev/docs/cli/enterprise/monitor-and-track/prompt-logging)

---

## Control de herramientas web

Los administradores pueden deshabilitar las herramientas web (`web_search` y `web_fetch`) para todos los usuarios:

1. Abrir la **Consola Kiro**
2. Vaya a **Configuración → Configuración compartida**
3. Desactivar **Herramientas de búsqueda y recuperación web**

Cuando están deshabilitados, los usuarios ven una notificación en `/tools` indicando que el administrador deshabilitó el acceso web.

---

## Controles de monitoreo disponibles

| Controlar | Descripción |
|---|---|
| **Panel de uso** | Uso agregado de la organización |
| **Actividad por usuario** | actividad individual |
| **Registro rápido** | Auditoría de avisos |
| **Estados de suscripción** | Activo / Cancelado / Pendiente por usuario |