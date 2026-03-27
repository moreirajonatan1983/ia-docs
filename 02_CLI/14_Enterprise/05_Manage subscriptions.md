# Administrar suscripciones

> **Fuente:** [kiro.dev/docs/cli/enterprise/subscription-management/](https://kiro.dev/docs/cli/enterprise/subscription-management/)

---

## Cambiar los planes de suscripción de Kiro

1. Iniciar sesión en **AWS Management Console**
2. Navegar a la **Kiro Console** (si no la ves, verificará la región de AWS)
3. Vaya a **Usuarios y Grupos → pestaña Usuarios o Grupos**
4. Seleccionar el usuario o grupo
5. Elegir **Cambiar plan** → seleccionar el nuevo plan → **Continuar**

**Tiempo:**
- **Upgrade** (plan mayor): cambios **inmediatos**
- **Downgrade** (plan menor): cambios al **inicio del próximo mes**

Ver [Facturación empresarial →](./09_Billing.md) para detalles sobre qué incluye cada nivel.

---

## Darse de baja de usuarios de Kiro

1. Iniciar sesión en **AWS Management Console**
2. Navegar a la **Consola Kiro**
3. Vaya a **Usuarios y Grupos → pestaña Usuarios o Grupos**
4. Seleccionar el usuario o grupo a cancelar
5. Elegir **Desactivar plan** → revisar el diálogo → **Cancelar suscripción**

> Después de cancelar, la suscripción se marca como **Cancelada**. El pierde acceso **inmediatamente** a las características pagas de los usuarios.

---

## Eliminación automática de suscripción

Las suscripciones pueden eliminarse automáticamente cuando:
- Un usuario es eliminado del proveedor de identidad.
- Un usuario es eliminado del grupo suscrito

---

## Habilitar excedentes para usuarios de Kiro

El excedente permite a los usuarios continuar trabajando cuando superan los límites de su plan.

**Ventajas:**
- ✅ **Productividad ininterrumpida** durante picos de uso
- ✅ **Mejor comprensión del uso real** para dimensionar futuras suscripciones

**Por defecto, el exceso está deshabilitado.** Una vez habilitado, aplica a **todos los usuarios y grupos del perfil**.

Para habilitar:
1. Iniciar sesión en **AWS Management Console**
2. Navegar a la **Consola Kiro**
3. Vaya a **Configuración**
4. En la sección **Configuración de Kiro**, activa **Excedentes**

> Los tapones personalizados de excedente no están disponibles aún (próximamente).

---

## Estados de suscripción

| Estado | Descripción | ¿Se cobra? |
|---|---|---|
| **Activo** | Suscrito y activo | ✅Sí |
| **Cancelado** | Cancelado por admin | ❌ No |
| **Pendiente** | Suscrito sin activar | ❌ No |