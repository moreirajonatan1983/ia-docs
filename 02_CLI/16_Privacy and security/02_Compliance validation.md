# Validación de cumplimiento

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/compliance/](https://kiro.dev/docs/cli/privacy-and-security/compliance/)

---

## Descripción general

AWS, como proveedor de Kiro, mantiene una amplia gama de certificaciones de cumplimiento y programas de seguridad. La responsabilidad compartida entre AWS y el cliente aplica al uso de Kiro.

---

## Programas de cumplimiento de AWS

Kiro está construido sobre la infraestructura de AWS, la cual cuenta con certificaciones de seguridad y cumplimiento reconocidas globalmente:

| Programa | Descripción |
|---|---|
| **SOC 1, 2, 3** | Informes de Control de Organización de Servicios |
| **ISO 27001** | Gestión de Seguridad de la Información |
| **ISO 27017** | Controles de seguridad en la nube |
| **ISO 27018** | Protección de Datos Personales en la Nube |
| **PCI DSS** | Estándar de seguridad de datos de la industria de tarjetas de pago |
| **FedRAMP** | Programa Federal de Gestión de Riesgos y Autorizaciones (Gobierno de EE. UU.) |
| **RGPD** | Reglamento General de Protección de Datos (UE) |
| **HIPAA** | Ley de Responsabilidad y Portabilidad del Seguro Médico |

---

## Modelo de responsabilidad compartida

AWS opera bajo el **Modelo de Responsabilidad Compartida**:

| Responsabilidad de AWS | Responsabilidad del Cliente |
|---|---|
| Seguridad física de centros de datos | Gestión de credenciales y accesos |
| Infraestructura de red | Configuración de permisos IAM |
| Hipervisor y hardware | Datos que se envían a Kiro |
| Cifrado en tránsito y en reposo | Cumplimiento de las regulaciones locales |

---

## Cumplimiento empresarial

Los usuarios de Enterprise tienen controles adicionales:
- **Exclusión automática de telemetría** — Datos no usados para mejora del servicio
- **Registro rápido** — Para auditoría interna
- **Cifrado en reposo configurable** — Control adicional sobre cifrado de datos
- **Selección de región** — Control sobre dónde se almacenan los datos

---

## Residencia de datos

La región donde se crea el Kiro Profile determina dónde se almacenan los datos. Ver [regiones soportadas →](../14_Enterprise/11_supportedregions.md) para más detalles.

---

## Recursos adicionales

- [Programas de cumplimiento de AWS →](https://aws.amazon.com/compliance/programs/)
- [Aviso de privacidad de AWS →](https://aws.amazon.com/privacy/)
- [Política de privacidad de Kiro →](https://aws.amazon.com/privacy/)
- [Política de IA responsable de AWS →](https://aws.amazon.com/ai/responsible-ai/policy/)