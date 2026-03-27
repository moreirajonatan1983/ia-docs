# Conceptos empresariales

> **Fuente:** [kiro.dev/docs/enterprise/concepts/](https://kiro.dev/docs/enterprise/concepts/)

---

Glosario de términos clave para administradores que gestionan suscripciones y usuarios de Kiro Enterprise.

---

## Referencia de conceptos

| Término | Definición |
|---|---|
| **Centro de identidad de AWS IAM** | Servicio AWS que proporciona un lugar central para gestionar las identidades de usuarios de Kiro |
| **Región de AWS** | Ubicación física donde AWS agrupa sus centros de datos. Relevante en dos dimensiones: (1) región donde está habilitado IAM Identity Center, y (2) región donde se crea el perfil de Kiro (donde se almacenan los datos) |
| **Grupo** | Colección de usuarios dentro de IAM Identity Center. Al suscribir un grupo a Kiro, los usuarios individuales se suscriben por separado (no existe concepto de suscripción grupal) |
| **Consola Kiro** | Consola dentro de la consola AWS donde crearás y gestionarás suscripciones Kiro y configurarás ajustes. Aparece como "Kiro" en el menú desplegable de servicios AWS |
| **Créditos de Kiro** | Unidad de consumo que mide el uso de las características de IA de Kiro. Se gastan en interacciones con IA y se reponen según el nivel de suscripción |
| **Usuario empresarial de Kiro** | Usuario que fue agregado y suscrito a un nivel de Kiro a través de la consola AWS, con acceso mediante IAM Identity Center, Okta o Microsoft Entra ID |
| **Perfil de Kiro** | Abstracción de gestión que define y aplicaciones configuraciones administrativas y suscripciones a usuarios empresariales en una cuenta AWS y región determinadas. Una cuenta AWS + región = un único perfil. Se configura desde la consola Kiro |
| **Nivel de suscripción de Kiro** | Plan de precios con una cantidad predeterminada de créditos Kiro (Free, Pro, Pro+, Power) |