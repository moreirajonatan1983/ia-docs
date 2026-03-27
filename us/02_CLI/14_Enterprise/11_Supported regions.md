# Supported Regions

> **Source:** [kiro.dev/docs/cli/enterprise/supported-regions/](https://kiro.dev/docs/cli/enterprise/supported-regions/)

---

## Overview

Kiro Enterprise opera en regiones específicas de AWS. Al configurar tu **Kiro Profile**, tenés que tener en cuenta dos tipos de regiones:

1. **Región de IAM Identity Center** — Donde se gestionan las identidades de usuario y se almacenan las suscripciones
2. **Región del Kiro Profile** — Donde se almacenan los datos de usuario (puede ser diferente)

---

## Important Notes on Regions

- Si usás **IAM Identity Center**, la región donde está habilitada tu instancia es donde se gestionan las identidades
- La región del **Kiro Profile** es donde se almacenan los datos — puede ser una región diferente a la de IAM Identity Center
- Si no ves la **Kiro Console** en la AWS Console, verificá que estás en la **AWS Region correcta**

---

## Selecting the Right Region

Al configurar Kiro Enterprise:
1. Verificá en qué región está habilitada tu instancia de IAM Identity Center
2. Elegí la región del Kiro Profile según dónde querés almacenar los datos
3. Asegurate de que la región del Kiro Profile sea consistente con tus requisitos de residencia de datos y compliance

---

## Data Residency Considerations

La región donde se crea el Kiro Profile determina dónde se almacenan los datos de los usuarios. Considerá:
- **Requisitos contractuales** de residencia de datos
- **Regulaciones locales** (ej. GDPR en Europa)
- **Latencia** para los usuarios finales

---

## Related

- [Concepts →](./01_Concepts.md) — Definición de AWS Region en el contexto de Kiro
- [Privacy and Security →](https://kiro.dev/docs/cli/privacy-and-security/)
- [AWS Regions documentation →](https://docs.aws.amazon.com/general/latest/gr/rande.html)