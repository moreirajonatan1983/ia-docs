# Data Protection

> **Source:** [kiro.dev/docs/privacy-and-security/data-protection/](https://kiro.dev/docs/privacy-and-security/data-protection/)

---

## Data Storage

Kiro almacena tus preguntas, sus respuestas y contexto adicional (como código) para generar nuevas respuestas.

| Tipo de usuario | Dónde se almacena el contenido |
|---|---|
| **Free tier / Individual subscriber** | US East (N. Virginia) |
| **Enterprise user** | Los datos **no se almacenan** |

Con cross-region inferencing, el contenido puede procesarse en una región diferente dentro de la misma geografía.

---

## Data Encryption

### Encryption in Transit
Toda la comunicación entre los clientes y Kiro, y entre Kiro y sus servicios downstream, está protegida con **TLS 1.2 o superior**.

### Encryption at Rest
- **Free / Individual:** Kiro cifra los datos usando **AWS owned encryption keys** de AWS KMS. No es necesaria ninguna acción por parte del usuario.
- **Enterprise:** Los administradores pueden crear **customer managed keys (CMK)** de KMS para cifrar los datos. Solo se soportan keys simétricas. El administrador debe proveer la key en la Kiro console para activarla.

---

## Service Improvement

AWS puede usar cierto contenido de usuarios **Free tier** e **individual subscribers** para mejorar el servicio:

| Tipo de usuario | Uso para mejora del servicio |
|---|---|
| **Free / Individual (social login / Builder ID)** | ✅ Puede usarse (prompts, código generado, respuestas) |
| **Enterprise user** | ❌ **No se usa** para mejora del servicio |
| **Amazon Q Developer Pro (via AWS account)** | ❌ **No se usa** para mejora del servicio |

---

## Opt Out of Data Sharing

Por defecto, Kiro recopila telemetría de uso, errores, crash reports y contenido de usuarios Free / individual subscribers.

> **Enterprise users:** están automáticamente excluídos de la recopilación de telemetría y contenido por AWS.

### Opting Out in the IDE

1. Abrí Settings en Kiro
2. Cambiá a la sub-pestaña **User**
3. Elegí **Application** → **Telemetry and Content**
4. Para excluirte de telemetría: desmarcá **Usage Analytics And Performance Metrics**
5. Para excluirte del contenido: desmarcá **Content Collection for Service Improvement**

### Opting Out in the CLI

1. Abrí **Preferences** en la app Kiro CLI
2. Para telemetría: desactivá el toggle **Telemetry**
3. Para contenido: desactivá el toggle **Share Kiro content with AWS**

---

## Types of Telemetry Collected

- **Usage data:** Versión de Kiro, sistema operativo (Windows, Linux, macOS), machine ID anónimo
- **Performance metrics:** Request count, errores y latencia para:
  - Login, Tab completion, Code generation, Steering, Hooks, Spec generation, Tools, MCP