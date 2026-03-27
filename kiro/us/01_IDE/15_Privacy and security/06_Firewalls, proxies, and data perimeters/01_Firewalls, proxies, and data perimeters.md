# Firewalls, Proxies, and Data Perimeters

> **Source:** [kiro.dev/docs/privacy-and-security/firewalls/](https://kiro.dev/docs/privacy-and-security/firewalls/)

---

## Network Traffic Overview

Kiro realiza dos tipos de conexiones salientes:

| Tipo | Descripción |
|---|---|
| **IDE traffic** | Requests del proceso Kiro (chat, completions, telemetría, updates, extensiones). Respeta la configuración de proxy del IDE |
| **Browser traffic** | El login abre el browser por defecto. Usa el network stack del OS y **bypasea** la configuración de proxy del IDE |

> ⚠️ Tu firewall debe permitir **ambos tipos** a nivel de red.

---

## Core URLs (Required)

Toda instalación de Kiro necesita las siguientes URLs (sign-in, chat, telemetría, auto-updates):

| URL | Propósito |
|---|---|
| `app.kiro.dev` | Sign-in y portal |
| `prod.us-east-1.auth.desktop.kiro.dev` | Autenticación |
| `prod.us-east-1.telemetry.desktop.kiro.dev` | Telemetría |
| `prod.download.desktop.kiro.dev` | Actualizaciones |
| `q.us-east-1.amazonaws.com` | API backend (N. Virginia) |
| `q.eu-central-1.amazonaws.com` | API backend (Frankfurt) |

> 💡 Si tu política de red permite wildcards, podés usar `*.kiro.dev` en lugar de los primeros 4 dominios.

---

## IAM Identity Center URLs

Si tu organización usa **AWS IAM Identity Center**:

```
<idc-directory-id-or-alias>.awsapps.com
oidc.<sso-region>.amazonaws.com
```

Reemplazá `idc-directory-id-or-alias` con el ID o alias de tu instancia IAM Identity Center, y `sso-region` con la región AWS donde está habilitada.

---

## External Identity Providers

Si usás un IdP externo (Okta o Microsoft Entra ID):

```
login.microsoftonline.com     # Microsoft Entra ID
<your-org>.okta.com           # Okta
```

Consultá con tu equipo de identidad si no estás seguro del dominio exacto.

---

## AWS GovCloud

Para **AWS GovCloud (US)**, usá estos endpoints FIPS-compliant en lugar de los Core URLs:

```
q-fips.us-gov-east-1.amazonaws.com
q-fips.us-gov-west-1.amazonaws.com
```

---

## Subscription Management URLs

Si usás login social (Google, GitHub, AWS Builder ID), Kiro usa **Stripe** para la facturación:

```
billing.stripe.com
checkout.stripe.com
```

> ℹ️ Los clientes Enterprise con IAM Identity Center no necesitan estos dominios.

---

## Optional URLs

Solo necesitás estas URLs si usás las features correspondientes:

| URL | Feature |
|---|---|
| `open-vsx.org` | Extensiones |
| `openvsx.eclipsecontent.org` | Extensiones |
| `github.com` | Powers |
| `raw.githubusercontent.com` | Powers |

---

## Proxy Configuration

Kiro respeta las variables de entorno estándar de proxy para todo el tráfico del IDE:

```
HTTP_PROXY
HTTPS_PROXY
NO_PROXY
```

También podés configurar el proxy desde **Settings → Proxy** dentro de Kiro.

> ⚠️ El tráfico del browser (sign-in) usa el network stack del OS — el proxy del IDE **no aplica**. Tu firewall debe permitir las URLs de IAM Identity Center y `app.kiro.dev` a nivel de red.

---

## Data Perimeters

Si usás [data perimeters en AWS](https://aws.amazon.com/identity/data-perimeters-on-aws/), asegurate de que tus políticas permitan a los service principals de Kiro acceder a los endpoints listados en esta página.

Para controles a nivel de VPC: [VPC Endpoints (AWS PrivateLink) →](./07_VPC%20endpoints%20(AWS%20PrivateLink).md)