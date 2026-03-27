# Protección de datos

> **Fuente:** [kiro.dev/docs/privacy-and-security/data-protection/](https://kiro.dev/docs/privacy-and-security/data-protection/)

---

## Almacenamiento de datos

Kiro almacena tus preguntas, sus respuestas y contexto adicional (como código) para generar nuevas respuestas.

| Tipo de usuario | Dónde se almacena el contenido |
|---|---|
| **Nivel gratuito / Suscriptor individual** | Este de EE. UU. (Norte de Virginia) |
| **Usuario empresarial** | Los datos **no se almacenan** |

Con la inferencia entre regiones, el contenido puede procesarse en una región diferente dentro de la misma geografía.

---

## Cifrado de datos

### Cifrado en tránsito
Toda la comunicación entre los clientes y Kiro, y entre Kiro y sus servicios downstream, está protegida con **TLS 1.2 o superior**.

### Cifrado en reposo
- **Gratis / Individual:** Kiro cifra los datos usando **claves de cifrado propiedad de AWS** de AWS KMS. No es necesaria ninguna acción por parte del usuario.
- **Enterprise:** Los administradores pueden crear **claves administradas por el cliente (CMK)** de KMS para cifrar los datos. Solo se soportarán teclas simétricas. El administrador debe proporcionar la llave en la consola Kiro para activarla.

---

## Mejora del servicio

AWS puede usar cierto contenido de usuarios **Nivel gratuito** y **suscriptores individuales** para mejorar el servicio:

| Tipo de usuario | Uso para mejorar el servicio |
|---|---|
| **Gratis / Individual (inicio de sesión social / ID de constructor)** | ✅ Puede usar (prompts, código generado, respuestas) |
| **Usuario empresarial** | ❌ **No se usa** para mejorar el servicio |
| **Amazon Q Developer Pro (a través de una cuenta de AWS)** | ❌ **No se usa** para mejorar el servicio |

---

## Optar por no compartir datos

Por defecto, Kiro recopila telemetría de uso, errores, informes de fallos y contenido de usuarios Suscriptores gratuitos/individuales.

> **Usuarios empresariales:** están automáticamente excluidos de la recopilación de telemetría y contenido por AWS.

### Optar por no participar en el IDE

1. Abrir configuración en Kiro
2. Cambiá a la sub-pestaña **Usuario**
3. Elegí **Aplicación** → **Telemetría y Contenido**
4. Para excluirte de telemetría: desmarca **Usage Analytics And Performance Metrics**
5. Para excluirte del contenido: desmarca **Recopilación de contenido para mejorar el servicio**

### Optar por no participar en la CLI

1. Abrí **Preferencias** en la aplicación Kiro CLI
2. Para telemetría: desactive el botón **Telemetría**
3. Para contenido: desactivá el interruptor **Compartir contenido de Kiro con AWS**

---

## Tipos de telemetría recopilados

- **Datos de uso:** Versión de Kiro, sistema operativo (Windows, Linux, macOS), ID de máquina anónimo
- **Métricas de rendimiento:** Recuento de solicitudes, errores y latencia para:
  - Inicio de sesión, finalización de pestañas, generación de código, dirección, hooks, generación de Specs, herramientas, MCP