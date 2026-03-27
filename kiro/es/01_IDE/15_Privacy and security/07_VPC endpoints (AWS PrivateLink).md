# Puntos de enlace de la VPC (AWS PrivateLink)

> **Fuente:** [kiro.dev/docs/privacy-and-security/vpc-endpoints/](https://kiro.dev/docs/privacy-and-security/vpc-endpoints/)

---

AWS PrivateLink permite establecer una **conexión privada** entre tu VPC y Kiro, sin que el tráfico atraviese la Internet pública.

---

## Consideraciones

Antes de configurar un endpoint de VPC para Kiro, revise las [limitaciones de endpoints de interfaz](https://docs.aws.amazon.com/vpc/latest/privatelink/create-interface-endpoint.html#vpce-interface-limitations) en la guía de Amazon VPC.

Kiro soporta llamadas a todas sus acciones de API desde tu VPC, en el contexto de servicios configurados para trabajar con Kiro.

---

## Requisitos previos

- Cuenta AWS con permisos para crear y configurar recursos
- Una VPC ya creada en tu cuenta AWS
- Familiaridad con Amazon VPC y Kiro

---

## Creación de un endpoint de interfaz VPC para Kiro

Puede crear el endpoint de VPC usando la **consola de Amazon VPC** o la **AWS CLI**.

Referencia: [Creación de un endpoint de interfaz →](https://docs.aws.amazon.com/vpc/latest/privatelink/create-interface-endpoint.html#create-interface-endpoint)

### Nombres de servicios para Kiro

| endpoint | Región |
|---|---|
| `com.amazonaws.us-east-1.q` | Este de EE. UU. (Norte de Virginia) |
| `com.amazonaws.us-east-1.codewhisperer` | Este de EE. UU. (Norte de Virginia) — en solitario |
| `com.amazonaws.eu-central-1.q` | Europa (Fráncfort) |
| `com.amazonaws.us-gov-west-1.q` | AWS GovCloud (EE.UU.-Oeste) |
| `com.amazonaws.us-gov-east-1.q` | AWS GovCloud (EE.UU.-Este) |

> ℹ️ Kiro soporta perfiles de desarrolladores de Amazon Q en EE.UU. Este (N. Virginia) y Europa (Frankfurt). El endpoint Amazon CodeWhisperer solo está disponible en el este de EE. UU.

### DNS privado

Si habilita DNS privado para el endpoint, podrá hacer solicitudes a Kiro usando su nombre DNS por defecto para la región. Ejemplo:

```
q.us-east-1.amazonaws.com
```

---

## Uso de una computadora local

Para conectar a Kiro desde un equipo local a través de AWS PrivateLink:

1. **Crea una conexión VPN** entre tu dispositivo local y tu VPC
   - [Guía del usuario del cliente VPN de AWS →](https://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-user-what-is.html)

2. **Crear el endpoint de la VPC de interfaz** para Kiro
   - [Instrucciones arriba ↑](#creando-una-interfaz-vpc-endpoint-para-kiro)

3. **Configurar un endpoint entrante de Amazon Route 53**
   - Esto permite usar el nombre DNS del endpoint de Kiro desde tu dispositivo local
   - [Enrutamiento a un endpoint de interfaz VPC →](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-to-vpc-interface-endpoint.html)