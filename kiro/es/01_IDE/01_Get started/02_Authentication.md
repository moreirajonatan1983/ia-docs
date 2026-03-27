# Métodos de autenticación

> **Fuente:** [kiro.dev/docs/getting-started/authentication/](https://kiro.dev/docs/getting-started/authentication/)
> **Página actualizada:** 19 de marzo de 2026

---

Kiro admite los siguientes proveedores de autenticación:

- **GitHub:** Integración perfecta con tu cuenta de GitHub.
- **Google:** Iniciá sesión con tus credenciales de Google.
- **AWS Builder ID:** Configuración rápida para desarrolladores individuales.
- **AWS IAM Identity Center:** Autenticación de nivel empresarial.
- **Proveedor de identidad externo:** Conectate a través del proveedor de identidad de tu organización (por ejemplo, Microsoft Entra ID u Okta).

> **Información:** Los usuarios que tienen una suscripción paga de Kiro y acceden a ella a través de un proveedor de inicio de sesión social (como GitHub o Google) o mediante AWS Builder ID se consideran **suscriptores individuales**. Podemos utilizar cierto contenido de Kiro Free Tier y de suscriptores individuales de Kiro para mejorar el servicio. Para obtener más información sobre la mejora del servicio y cómo darse de baja, consultá [Mejora del servicio](https://kiro.dev/docs/privacy-and-security/data-protection/#service-improvement).

Kiro es una aplicación de AWS que funciona como un IDE agente independiente **sin necesidad de configurar una cuenta de AWS**. Podés descargar y usar Kiro inmediatamente sin ninguna configuración de cuenta externa: maneja las interacciones de IA y la asistencia de código directamente a través de la propia aplicación. Ya sea que estés desarrollando con otros servicios de AWS o no, podés aprovechar todas las capacidades de Kiro para mejorar tu flujo de trabajo de desarrollo.

---

## Métodos de autenticación disponibles

### GitHub

Utilizá las siguientes instrucciones para Sign in en Kiro usando GitHub.

**Para Sign in con GitHub:**

1. En Kiro, elegí **Sign in with GitHub**. Serás redirigido a tu navegador web predeterminado para completar el proceso de inicio de sesión.
2. Ingresá tu nombre de usuario o dirección de correo electrónico y tu contraseña y luego elegí **Sign in**.
3. Elegí **Authorize kirodotdev** para autorizar la aplicación de Kiro con tu cuenta de GitHub.

---

### Google

Utilizá las siguientes instrucciones para Sign in en Kiro mediante Google.

**Para Sign in con Google:**

1. En Kiro, elegí **Sign in with Google**. Serás redirigido a tu navegador web predeterminado para completar el proceso de inicio de sesión.
2. Elegí una cuenta de Google que quieras usar con Kiro.
3. Elegí **Continue** para autorizar la aplicación de Kiro con tu cuenta de Google.

---

### AWS Builder ID

Utilizá las siguientes instrucciones para Sign in en Kiro usando AWS Builder ID.

**Para Sign in con AWS Builder ID:**

1. En Kiro, elegí **Login with AWS Builder ID**. Serás redirigido a tu navegador web predeterminado para completar el proceso de inicio de sesión.
2. Ingresá tu dirección de correo electrónico y luego elegí **Next**.
3. Ingresá tu contraseña y luego elegí **Sign in**.
4. Elegí **Allow access** para autorizar la aplicación de Kiro.

---

### AWS IAM Identity Center

Utilizá las siguientes instrucciones para Sign in en Kiro en tu organización, incluyendo AWS GovCloud (Estados Unidos), mediante AWS IAM Identity Center.

**Para Sign in con AWS IAM Identity Center:**

1. En Kiro, elegí **Sign in with AWS IAM Identity Center**.
2. En **Start URL**, ingresá la URL de inicio proporcionada por tu administrador o mesa de ayuda.
3. En **Region**, ingresá la región de AWS que aloja el directorio de identidad y luego elegí **Continue**.

> **Información:** Los métodos de autenticación admitidos en las regiones de AWS GovCloud (US) son **AWS IAM Identity Center** y **proveedores de identidad externos**. Los métodos de inicio de sesión individuales, como GitHub, Google y AWS Builder ID **no están disponibles** en las regiones de AWS GovCloud (US).
>
> Los usuarios saben que usarán Kiro con AWS GovCloud (US) asegurándose de que la URL de inicio utilizada durante la autenticación contenga `"us-gov-home"`, por ejemplo:
> ```
> https://start.us-gov-home.awsapps.com/directory/d-XXXXXXXXXX
> ```
>
> Kiro utiliza la misma descarga/instalador para las regiones comerciales y AWS GovCloud (US). La autenticación del IAM Identity Center enruta automáticamente el tráfico a la región adecuada de AWS GovCloud (US). Son necesarias las versiones **Kiro IDE 0.9.2+** y **Kiro CLI 1.25.0+** para la compatibilidad con las regiones de AWS GovCloud (US).

---

### Proveedor de identidad externo

Utilizá las siguientes instrucciones para Sign in en Kiro utilizando el proveedor de identidad externo de tu organización, como Microsoft Entra ID u Okta.

**Para Sign in con el proveedor de identidad de tu organización:**

1. En Kiro, elegí **Your organization**.
2. Ingresá tu correo electrónico de trabajo para encontrar tu organización y luego elegí **Continue**.
3. Completá el proceso de inicio de sesión con el proveedor de identidad de tu organización.

---

## Solucionar problemas de autenticación

Si encontrás problemas durante el proceso de autenticación, como fallos de redireccionamiento del navegador o errores de inicio de sesión, consultá nuestra [guía de solución de problemas](https://kiro.dev/docs/getting-started/authentication/#troubleshooting-authentication-issues) para obtener resoluciones específicas a tu plataforma y correcciones comunes.

---

## Próximos pasos

- [Revisar preguntas frecuentes →](https://kiro.dev/faq)
- [Explorar funciones del Agente →](https://kiro.dev/docs/chat)
- [Comenzar con Kiro →](https://kiro.dev/docs)