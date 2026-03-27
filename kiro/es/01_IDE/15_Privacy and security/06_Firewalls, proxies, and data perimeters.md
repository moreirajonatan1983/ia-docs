# Firewalls, proxies y perímetros de datos

> **Fuente:** [kiro.dev/docs/privacy-and-security/firewalls/](https://kiro.dev/docs/privacy-and-security/firewalls/)

---

## Descripción general del tráfico de red

Kiro realiza dos tipos de conexiones salientes:

| Tipo | Descripción |
|---|---|
| **Tráfico IDE** | Solicitudes del proceso Kiro (chat, completaciones, telemetría, actualizaciones, extensiones). Respeta la configuración de proxy del IDE |
| **Tráfico del navegador** | El inicio de sesión abre el navegador por defecto. Usa la pila de red del sistema operativo y **bypasea** la configuración de proxy del IDE |

> ⚠️ Tu firewall debe permitir **ambos tipos** a nivel de red.

---

## URL principales (obligatorias)

Toda instalación de Kiro necesita las siguientes URL (inicio de sesión, chat, telemetría, actualizaciones automáticas):

| URL | Propósito |
|---|---|
| `app.kiro.dev` | Iniciar sesión y portal |
| `prod.us-east-1.auth.desktop.kiro.dev` | Autenticación |
| `prod.us-east-1.telemetry.desktop.kiro.dev` | Telemetria |
| `prod.download.desktop.kiro.dev` | Actualizaciones |
| `q.us-east-1.amazonaws.com` | Backend API (Norte de Virginia) |
| `q.eu-central-1.amazonaws.com` | API backend (Fráncfort) |

> 💡 Si tu política de red permite comodines, podrás usar `*.kiro.dev` en lugar de los primeros 4 dominios.

---

## URL del Centro de identidad de IAM

Si tu organización usa **AWS IAM Identity Center**:

```
<idc-directory-id-or-alias>.awsapps.com
oidc.<sso-region>.amazonaws.com
```

Reemplazá `idc-directory-id-or-alias` con el ID o alias de tu instancia IAM Identity Center, y `sso-region` con la región AWS donde está habilitada.

---

## Proveedores de identidad externos

Si utiliza un IdP externo (Okta o Microsoft Entra ID):

```
login.microsoftonline.com     # Microsoft Entra ID
<your-org>.okta.com           # Okta
```

Consulta con tu equipo de identidad si no estás seguro del dominio exacto.

---

## AWS GovCloud

Para **AWS GovCloud (US)**, usaremos estos puntos finales compatibles con FIPS en lugar de las URL principales:

```
q-fips.us-gov-east-1.amazonaws.com
q-fips.us-gov-west-1.amazonaws.com
```

---

## URL de gestión de suscripciones

Si usás login social (Google, GitHub, AWS Builder ID), Kiro usa **Stripe** para la facturación:

```
billing.stripe.com
checkout.stripe.com
```

> ℹ️ Los clientes Enterprise con IAM Identity Center no necesitan estos dominios.

---

## URL opcionales

Solo necesitas estas URL si usamos las características correspondientes:

| URL | Característica |
|---|---|
| `open-vsx.org` | Extensiones |
| `openvsx.eclipsecontent.org` | Extensiones |
| `github.com` | Powers |
| `raw.githubusercontent.com` | Powers |

---

## Configuración de proxy

Kiro respeta las variables de entorno estándar de proxy para todo el tráfico del IDE:

```
HTTP_PROXY
HTTPS_PROXY
NO_PROXY
```

También puedes configurar el proxy desde **Configuración → Proxy** dentro de Kiro.

> ⚠️ El tráfico del navegador (iniciar sesión) usa la pila de red del sistema operativo — el proxy del IDE **no aplica**. Tu firewall debe permitir las URL de IAM Identity Center y `app.kiro.dev` a nivel de rojo.

---

## Perímetros de datos

Si usas [perímetros de datos en AWS](https://aws.amazon.com/identity/data-perimeters-on-aws/), asegúrate de que tus políticas permiten a los principales de servicio de Kiro acceder a los endpoints listados en esta página.

Para controlar el nivel de VPC: [VPC Endpoints (AWS PrivateLink) →](./07_VPC%20endpoints%20(AWS%20PrivateLink).md)