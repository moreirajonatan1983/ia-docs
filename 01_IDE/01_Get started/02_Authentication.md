# Métodos de autenticación

> **Fuente:** [kiro.dev/docs/getting-started/authentication/](https://kiro.dev/docs/getting-started/authentication/)
> **Página actualizada:** 19 de marzo de 2026

---

Kiro admite los siguientes proveedores de autenticación:

| Proveedor | Descripción |
|---|---|
| **GitHub** | Integración perfecta con su cuenta de GitHub |
| **Google** | Inicia sesión con tus credenciales de Google |
| **ID del creador de AWS** | Configuración rápida para desarrolladores individuales |
| **Centro de identidad de AWS IAM** | Autenticación de nivel empresarial |
| **Proveedor de identidad externo** | Conéctese a través del IdP de su organización (por ejemplo, Microsoft Entra ID u Okta) |

> **Información:** Los usuarios que tienen una suscripción paga de Kiro y acceden a ella a través de un proveedor de inicio de sesión social (como GitHub o Google) o mediante AWS Builder ID se consideran **suscriptores individuales**. Podemos utilizar cierto contenido de Kiro Free Tier y de suscriptores individuales de Kiro para mejorar el servicio. Para obtener más información sobre la mejora del servicio y cómo darse de baja, consulte [Mejora del servicio](https://kiro.dev/docs/privacy-and-security/).

Kiro es una aplicación de AWS que funciona como un IDE agente independiente **sin necesidad de configurar una cuenta de AWS**. Puede descargar y usar Kiro inmediatamente sin ninguna configuración de cuenta externa: maneja las interacciones de IA y la asistencia de código directamente a través de la propia aplicación.

---

## Métodos de autenticación disponibles

### GitHub

Utilice las siguientes instrucciones para iniciar sesión en Kiro usando GitHub.

**Para iniciar sesión con GitHub:**

1. En Kiro, elija **Iniciar sesión con GitHub**. Serás redirigido a tu navegador web predeterminado para completar el proceso de inicio de sesión.
2. Ingrese su nombre de usuario o dirección de correo electrónico y su contraseña y luego elija **Iniciar sesión**.
3. Elija **Autorizar kirodotdev** para autorizar la aplicación Kiro con su cuenta de GitHub.

---

### Google

Utilice las siguientes instrucciones para iniciar sesión en Kiro mediante Google.

**Para iniciar sesión con Google:**

1. En Kiro, elija **Iniciar sesión con Google**. Serás redirigido a tu navegador web predeterminado para completar el proceso de inicio de sesión.
2. Elige una cuenta de Google que quieras usar con Kiro.
3. Elija **Continuar** para autorizar la aplicación Kiro con su cuenta de Google.

---

### ID del creador de AWS

Utilice las siguientes instrucciones para iniciar sesión en Kiro utilizando AWS Builder ID.

**Para iniciar sesión con AWS Builder ID:**

1. En Kiro, elija **Iniciar sesión con AWS Builder ID**. Serás redirigido a tu navegador web predeterminado para completar el proceso de inicio de sesión.
2. Ingrese su dirección de correo electrónico y luego elija **Siguiente**.
3. Ingrese su contraseña y luego elija **Iniciar sesión**.
4. Elija **Permitir acceso** para autorizar la aplicación Kiro.

---

### Centro de identidad de AWS IAM

Utilice las siguientes instrucciones para iniciar sesión en Kiro en su organización, incluido AWS GovCloud (EE. UU.), mediante AWS IAM Identity Center.

**Para iniciar sesión con AWS IAM Identity Center:**

1. En Kiro, elija **Iniciar sesión con AWS IAM Identity Center**.
2. En **URL de inicio**, ingrese la URL de inicio proporcionada por su administrador o servicio de asistencia.
3. En **Región**, ingrese la región de AWS que aloja el directorio de identidad y luego elija **Continuar**.

> **Información:** Los métodos de autenticación admitidos en las regiones de AWS GovCloud (EE. UU.) son **AWS IAM Identity Center** y **proveedores de identidad externos**. Los métodos de inicio de sesión individuales, como GitHub, Google y AWS Builder ID **no están disponibles** en las regiones de AWS GovCloud (EE. UU.).
>
> Los usuarios saben que usarán Kiro con AWS GovCloud (EE. UU.) asegurándose de que la URL de inicio utilizada durante la autenticación contenga `"us-gov-home"`, por ejemplo:
> ```
> https://start.us-gov-home.awsapps.com/directory/d-XXXXXXXXXX
> ```
>
> Kiro utiliza la misma descarga/instalador para las regiones comerciales y AWS GovCloud (EE. UU.). La autenticación de IAM Identity Center enruta automáticamente el tráfico a la región adecuada de AWS GovCloud (EE. UU.). **Kiro IDE versión 0.9.2+** y **Kiro CLI versión 1.25.0+** son necesarios para la compatibilidad con las regiones de AWS GovCloud (EE. UU.).

---

### Proveedor de identidad externo

Utilice las siguientes instrucciones para iniciar sesión en Kiro utilizando el proveedor de identidad externo de su organización, como Microsoft Entra ID u Okta.

**Para iniciar sesión con el proveedor de identidad de su organización:**

1. En Kiro, elige **Tu organización**.
2. Ingrese su correo electrónico de trabajo para encontrar su organización y luego elija **Continuar**.
3. Complete el proceso de inicio de sesión con el proveedor de identidad de su organización.

---

## Solución de problemas de autenticación

Si encuentra problemas durante el proceso de autenticación, como fallas de redireccionamiento del navegador o errores de inicio de sesión, consulte nuestra [guía de solución de problemas](https://kiro.dev/docs/troubleshooting/#authentication-issues) para obtener soluciones específicas de la plataforma y correcciones comunes.

---

## Próximos pasos

- [Revisar preguntas frecuentes →](https://kiro.dev/faq)
- [Explorar funciones del Agente →](https://kiro.dev/docs/chat)
- [Comenzar con Kiro →](https://kiro.dev/docs)