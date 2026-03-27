# VPC Endpoints (AWS PrivateLink)

> **Source:** [kiro.dev/docs/privacy-and-security/vpc-endpoints/](https://kiro.dev/docs/privacy-and-security/vpc-endpoints/)

---

AWS PrivateLink permite establecer una **conexión privada** entre tu VPC y Kiro, sin que el tráfico atraviese la Internet pública.

---

## Considerations

Antes de configurar un VPC endpoint para Kiro, revisá las [limitaciones de interface endpoints](https://docs.aws.amazon.com/vpc/latest/privatelink/create-interface-endpoint.html#vpce-interface-limitations) en la guía de Amazon VPC.

Kiro soporta llamadas a todas sus acciones de API desde tu VPC, en el contexto de servicios configurados para trabajar con Kiro.

---

## Prerequisites

- Cuenta AWS con permisos para crear y configurar recursos
- Una VPC ya creada en tu cuenta AWS
- Familiaridad con Amazon VPC y Kiro

---

## Creating an Interface VPC Endpoint for Kiro

Podés crear el VPC endpoint usando la **Amazon VPC console** o la **AWS CLI**.

Referencia: [Creating an interface endpoint →](https://docs.aws.amazon.com/vpc/latest/privatelink/create-interface-endpoint.html#create-interface-endpoint)

### Service Names for Kiro

| Endpoint | Región |
|---|---|
| `com.amazonaws.us-east-1.q` | US East (N. Virginia) |
| `com.amazonaws.us-east-1.codewhisperer` | US East (N. Virginia) — solo |
| `com.amazonaws.eu-central-1.q` | Europe (Frankfurt) |
| `com.amazonaws.us-gov-west-1.q` | AWS GovCloud (US-West) |
| `com.amazonaws.us-gov-east-1.q` | AWS GovCloud (US-East) |

> ℹ️ Kiro soporta Amazon Q Developer profiles en US East (N. Virginia) y Europe (Frankfurt). El endpoint Amazon CodeWhisperer solo está disponible en US East.

### DNS Privado

Si habilitás private DNS para el endpoint, podés hacer requests a Kiro usando su nombre DNS por defecto para la región. Ejemplo:

```
q.us-east-1.amazonaws.com
```

---

## Using an On-Premises Computer

Para conectarte a Kiro desde un equipo on-premises a través de AWS PrivateLink:

1. **Crear una conexión VPN** entre tu dispositivo on-premises y tu VPC
   - [AWS VPN Client User Guide →](https://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-user-what-is.html)

2. **Crear el interface VPC endpoint** para Kiro
   - [Instrucciones arriba ↑](#creating-an-interface-vpc-endpoint-for-kiro)

3. **Configurar un inbound Amazon Route 53 endpoint**
   - Esto permite usar el nombre DNS del endpoint de Kiro desde tu dispositivo on-premises
   - [Routing to a VPC interface endpoint →](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-to-vpc-interface-endpoint.html)