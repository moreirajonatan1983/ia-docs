# Conceptos

> **Fuente:** [kiro.dev/docs/cli/enterprise/concepts/](https://kiro.dev/docs/cli/enterprise/concepts/)

---

Glosario de términos clave para administradores que gestionan suscripciones y usuarios de Kiro Enterprise.

---

## Centro de identidad de AWS IAM

Servicio de AWS que proporciona un lugar centralizado para gestionar las identidades de los suscriptores de Kiro.

---

## Región de AWS

Una ubicación física donde AWS agrupa sus centros de datos. Existen dos regiones relevantes para administradores de Kiro:

1. La región donde está habilitada tu instancia de IAM Identity Center (donde se gestionan identidades y se almacenan suscripciones)
2. La región donde se crea tu perfil de Kiro (donde se almacenan los datos — puede ser diferente)

Ver [regiones soportadas →](./11_regiones soportadas.md) para más información.

---

## Grupo

Una colección de usuarios dentro de IAM Identity Center. Al suscribir un grupo a Kiro, los usuarios dentro de él se suscriben **individualmente** (no existe el concepto de suscripción grupal).

---

## Consola Kiro

Una consola dentro de la Consola AWS donde los administradores crean y gestionan suscripciones de Kiro y controlan la configuración. Aparece como **"Kiro"** en el menú desplegable de servicios de AWS.

---

## Créditos Kiro

Unidad de consumo que mide el uso de las funcionalidades de AI de Kiro. Los créditos se gastan al interactuar con capacidades de AI y se reabastecen según el nivel de suscripción.

---

## Usuario empresarial de Kiro

Un que fue agregado y suscrito a un nivel de suscripción de usuario de Kiro a través de la Consola AWS. Puede acceder a Kiro mediante IAM Identity Center, Okta o Microsoft Entra ID.

---

## Perfil de Kiro

La abstracción de gestión que define y aplicaciones administrativas y suscripciones a usuarios empresariales en una cuenta y región de AWS específicas.

Características:
- Corresponde a una combinación de cuenta AWS (administración o miembro) + región
- Solo puede existir **un perfil por cuenta AWS en una región dada**
- Se configura a través de la Consola Kiro

---

## Nivel de suscripción de Kiro

Un plan de precios específico con un número predeterminado de créditos Kiro.

---

## Tabla resumen

| Concepto | Descripción breve |
|---|---|
| **Centro de identidad IAM** | Gestión centralizada de identidades |
| **Región de AWS** | Ubicación física de los centros de datos |
| **Grupo** | Colección de usuarios (suscripción individual) |
| **Consola Kiro** | UI en AWS Console para gestionar Kiro |
| **Créditos Kiro** | Unidad de consumo de IA |
| **Usuario empresarial** | Usuario suscrito vía Consola AWS |
| **Perfil de Kiro** | Abstracción de gestión por cuenta + región |
| **Nivel de suscripción** | Plan de precios con créditos predeterminados |