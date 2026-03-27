# Compliance Validation

> **Source:** [kiro.dev/docs/cli/privacy-and-security/compliance/](https://kiro.dev/docs/cli/privacy-and-security/compliance/)

---

## Overview

AWS, como proveedor de Kiro, mantiene una amplia gama de certificaciones de compliance y programas de seguridad. La responsabilidad compartida entre AWS y el cliente aplica al uso de Kiro.

---

## AWS Compliance Programs

Kiro está construido sobre la infraestructura de AWS, la cual cuenta con certificaciones de seguridad y compliance reconocidas globalmente:

| Programa | Descripción |
|---|---|
| **SOC 1, 2, 3** | Service Organization Control reports |
| **ISO 27001** | Information Security Management |
| **ISO 27017** | Cloud Security Controls |
| **ISO 27018** | Protection of Personal Data in the Cloud |
| **PCI DSS** | Payment Card Industry Data Security Standard |
| **FedRAMP** | Federal Risk and Authorization Management Program (US Gov) |
| **GDPR** | General Data Protection Regulation (EU) |
| **HIPAA** | Health Insurance Portability and Accountability Act |

---

## Shared Responsibility Model

AWS opera bajo el **Shared Responsibility Model**:

| Responsabilidad de AWS | Responsabilidad del Cliente |
|---|---|
| Seguridad física de data centers | Gestión de credenciales y accesos |
| Infraestructura de red | Configuración de permisos IAM |
| Hipervisor y hardware | Datos que se envían a Kiro |
| Cifrado en transit y at rest | Compliance con regulaciones locales |

---

## Enterprise Compliance

Los usuarios Enterprise tienen controles adicionales:
- **Exclusión automática de telemetría** — Datos no usados para mejora del servicio
- **Prompt logging** — Para auditoría interna
- **Encryption at rest configurable** — Control adicional sobre cifrado de datos
- **Region selection** — Control sobre dónde se almacenan los datos

---

## Data Residency

La región donde se crea el Kiro Profile determina dónde se almacenan los datos. Ver [Supported Regions →](../14_Enterprise/11_Supported regions.md) para más detalles.

---

## Additional Resources

- [AWS Compliance Programs →](https://aws.amazon.com/compliance/programs/)
- [AWS Privacy Notice →](https://aws.amazon.com/privacy/)
- [Kiro Privacy Policy →](https://aws.amazon.com/privacy/)
- [AWS Responsible AI Policy →](https://aws.amazon.com/ai/responsible-ai/policy/)