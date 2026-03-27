# Infrastructure Security

> **Source:** [kiro.dev/docs/privacy-and-security/infrastructure-security/](https://kiro.dev/docs/privacy-and-security/infrastructure-security/)

---

Como servicio gestionado, Kiro está protegido por la **seguridad de red global de AWS**.

---

## Transport Layer Security (TLS)

Los clientes que acceden a Kiro deben soportar:

- **TLS mínimo:** TLS 1.2
- **TLS recomendado:** TLS 1.3
- **Cipher suites:** Perfect Forward Secrecy: DHE o ECDHE

> ℹ️ La mayoría de los sistemas modernos (Java 7 y posterior) soportan estos modos.

---

## Request Authentication

Las requests deben estar firmadas usando:
- Un **Access Key ID** y **Secret Access Key** asociados a un IAM principal, o
- Credenciales de seguridad temporales generadas por **AWS Security Token Service (AWS STS)**

---

## AWS Resources

- [AWS Cloud Security](https://aws.amazon.com/security/)
- [Infrastructure Protection — AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/infrastructure-protection.html)