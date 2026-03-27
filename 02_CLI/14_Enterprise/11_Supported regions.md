# Regiones admitidas

> **Fuente:** [kiro.dev/docs/cli/enterprise/supported-regions/](https://kiro.dev/docs/cli/enterprise/supported-regions/)

---

## Descripción general

Kiro Enterprise opera en regiones específicas de AWS. Al configurar tu **Kiro Profile**, tendrás que tener en cuenta dos tipos de regiones:

1. **Región de IAM Identity Center** — Donde se gestionan las identidades de usuario y se almacenan las suscripciones
2. **Perfil Región del Kiro** — Donde se almacenan los datos de usuario (puede ser diferente)

---

## Notas importantes sobre las regiones

- Si usás **IAM Identity Center**, la región donde está habilitada tu instancia es donde se gestionan las identidades
- La región del **Kiro Profile** es donde se almacenan los datos — puede ser una región diferente a la de IAM Identity Center
- Si no ves la **Consola Kiro** en la Consola AWS, verifica que estés en la **Región AWS correcta**

---

## Seleccionar la región correcta

Al configurar Kiro Enterprise:
1. Verifique en qué región está habilitada su instancia de IAM Identity Center
2. Elegí la región del Kiro Profile según dónde querrás almacenar los datos
3. Asegurate de que la región del Kiro Profile sea consistente con tus requisitos de residencia de datos y cumplimiento

---

## Consideraciones de residencia de datos

La región donde se crea el Kiro Profile determina dónde se almacenan los datos de los usuarios. Considerá:
- **Requisitos contractuales** de residencia de datos
- **Regulaciones locales** (ej. GDPR en Europa)
- **Latencia** para los usuarios finales

---

## Relacionado

- [Concepts →](./01_Concepts.md) — Definición de región AWS en el contexto de Kiro
- [Privacidad y seguridad →](https://kiro.dev/docs/cli/privacy-and-security/)
- [Documentación de regiones de AWS →](https://docs.aws.amazon.com/general/latest/gr/rande.html)