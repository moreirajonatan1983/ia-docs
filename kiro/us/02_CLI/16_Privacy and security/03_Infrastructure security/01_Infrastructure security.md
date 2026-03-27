# Infrastructure Security

> **Source:** [kiro.dev/docs/cli/privacy-and-security/infrastructure-security/](https://kiro.dev/docs/cli/privacy-and-security/infrastructure-security/)

---

## Overview

Kiro está construido sobre la infraestructura global de AWS, diseñada con múltiples capas de controles de seguridad físicos, de red y operacionales.

---

## Physical Security

AWS mantiene seguridad física de nivel militar en sus data centers:
- Acceso biométrico y de múltiples factores
- Personal de seguridad 24/7
- CCTV y sistemas de detección de intrusiones
- Destrucción segura de medios físicos

---

## Network Security

| Medida | Descripción |
|---|---|
| **DDoS Protection** | AWS Shield Standard incluido (Shield Advanced disponible) |
| **Network Isolation** | VPCs con subnets privadas |
| **Traffic Filtering** | Security Groups y Network ACLs |
| **TLS Encryption** | Todo el tráfico cifrado en tránsito |
| **VPC Endpoints** | Comunicación privada sin salir a Internet público |

---

## Operational Security

- Monitoreo continuo de amenazas con **AWS GuardDuty**
- Logging centralizado con **AWS CloudTrail**
- Scanning de vulnerabilidades regular
- Equipo de seguridad dedicado (AWS Security)
- Programa de divulgación responsable de vulnerabilidades

---

## Kiro CLI Network Communication

El CLI Kiro se comunica únicamente con los endpoints de AWS:

```
api.kiro.dev         → API principal de Kiro
auth.kiro.dev        → Autenticación
```

Toda la comunicación usa **HTTPS/TLS 1.2+**.

---

## Firewall and Proxy Considerations

Si tu organización usa firewalls o proxies, necesitás permitir el tráfico a los endpoints de Kiro. Ver [Firewalls, proxies, and data perimeters →](./05_Firewalls, proxies, and data perimeters.md) para configuración detallada.

---

## Incident Response

AWS mantiene planes documentados de respuesta a incidentes de seguridad. En caso de un incidente de seguridad relacionado con Kiro:
1. Reportar a [Kiro billing support](https://app.kiro.dev/account/usage?support_form)
2. Revisar [AWS Security Bulletins](https://aws.amazon.com/security/security-bulletins/)
3. Seguir los procedimientos internos de respuesta a incidentes de tu organización