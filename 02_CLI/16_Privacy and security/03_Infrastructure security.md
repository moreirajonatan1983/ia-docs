# Seguridad de infraestructura

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/infrastructure-security/](https://kiro.dev/docs/cli/privacy-and-security/infrastructure-security/)

---

## Descripción general

Kiro está construido sobre la infraestructura global de AWS, diseñado con múltiples capas de controles de seguridad física, de red y operativas.

---

## Seguridad física

AWS mantiene seguridad física de nivel militar en sus centros de datos:
- Acceso biométrico y de múltiples factores
- Personal de seguridad 24/7
- CCTV y sistemas de detección de intrusiones.
- Destrucción segura de medios físicos

---

## Seguridad de la red

| Medida | Descripción |
|---|---|
| **Protección DDoS** | AWS Shield Standard incluido (Shield Advanced disponible) |
| **Aislamiento de red** | VPC con subredes privadas |
| **Filtrado de tráfico** | Grupos de Seguridad y ACL de Red |
| **Cifrado TLS** | Todo el tráfico cifrado en tránsito |
| **Puntos finales de VPC** | Comunicación privada sin salir a Internet público |

---

## Seguridad operativa

- Monitoreo continuo de amenazas con **AWS GuardDuty**
- Registro centralizado con **AWS CloudTrail**
- Escaneo de vulnerabilidades regular
- Equipo de seguridad dedicado (AWS Security)
- Programa de divulgación responsable de vulnerabilidades

---

## Comunicación de red Kiro CLI

El CLI Kiro se comunica únicamente con los endpoints de AWS:

```
api.kiro.dev         → API principal de Kiro
auth.kiro.dev        → Autenticación
```

Toda la comunicación usa **HTTPS/TLS 1.2+**.

---

## Consideraciones sobre firewall y proxy

Si tu organización utiliza firewalls o proxies, necesitarás permitir el tráfico a los endpoints de Kiro. Ver [Firewalls, proxies y perímetros de datos →](./05_Firewalls, proxies y perímetros de datos.md) para configuración detallada.

---

## Respuesta a incidentes

AWS mantiene planes documentados de respuesta a incidentes de seguridad. En caso de un incidente de seguridad relacionado con Kiro:
1. Reportar a [soporte de facturación de Kiro](https://app.kiro.dev/account/usage?support_form)
2. Revisar [Boletines de seguridad de AWS](https://aws.amazon.com/security/security-bulletins/)
3. Seguir los procedimientos internos de respuesta a incidentes de tu organización.