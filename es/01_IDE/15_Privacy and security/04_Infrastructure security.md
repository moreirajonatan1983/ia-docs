# Seguridad de infraestructura

> **Fuente:** [kiro.dev/docs/privacy-and-security/infrastructure-security/](https://kiro.dev/docs/privacy-and-security/infrastructure-security/)

---

Como servicio gestionado, Kiro está protegido por la **seguridad de red global de AWS**.

---

## Seguridad de la capa de transporte (TLS)

Los clientes que acceden a Kiro deben soportar:

| Requisito | Valor |
|---|---|
| **TLS mínimo** | TLS 1.2 |
| **TLS recomendado** | TLS 1.3 |
| **Suites de cifrado** | Secreto directo perfecto: DHE o ECDHE |

> ℹ️ La mayoría de los sistemas modernos (Java 7 y posteriores) soportan estos modos.

---

## Solicitar autenticación

Las solicitudes deben estar firmadas usando:
- Un **ID de clave de acceso** y **Clave de acceso secreta** asociados a un principal de IAM, o
- Credenciales de seguridad temporales generadas por **AWS Security Token Service (AWS STS)**

---

## Recursos de AWS

- [Seguridad en la nube de AWS](https://aws.amazon.com/security/)
- [Protección de infraestructura: marco de buena arquitectura de AWS] (https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/infrastructure-protection.html)