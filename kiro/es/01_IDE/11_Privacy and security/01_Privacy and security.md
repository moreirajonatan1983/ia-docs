# Privacidad y seguridad

> **Fuente:** [kiro.dev/docs/privacy-and-security/](https://kiro.dev/docs/privacy-and-security/)

---

Kiro proporciona varias funciones de seguridad para ayudarle a mantener el control sobre su entorno de desarrollo. Comprender estas características le ayudará a implementar medidas de seguridad adecuadas para sus necesidades específicas.

---

## Obtención de URL

En el módulo de chat de Kiro, puede pegar una URL específica para que su dispositivo la recupere y la use como contexto. Usted es responsable del contenido de la URL que obtiene y de asegurarse de que su uso cumpla con los términos y leyes de terceros aplicables.

---

## Piloto automático versus modo supervisado

Kiro opera en dos modos. **El piloto automático está habilitado de forma predeterminada.**

### Modo piloto automático

En modo Piloto automático, Kiro funciona **de forma autónoma**:
- Ejecuta múltiples pasos sin requerir aprobación para cada uno
- Toma decisiones basadas en su comprensión de sus requisitos.
- Incluye creación, modificación, búsqueda y eliminación de archivos.
- Puede ejecutar comandos que impactan el sistema de archivos
- Puedes activar o desactivar el piloto automático en la interfaz de chat en cualquier momento
- Puedes **interrumpir el piloto automático en cualquier momento** para recuperar el control manual

### Modo supervisado

En modo supervisado, Kiro trabaja **interactivamente** con el usuario:
- Sugiere acciones (creación, modificación, eliminación de archivos) pero **espera la commit del usuario** antes de continuar
- Hace preguntas aclaratorias cuando es necesario.
- Puedes revisar y aprobar cada documento generado o cambio de código.
- Mantiene el control total sobre el proceso de desarrollo.

### Ver y revertir cambios

En cualquier modo, puedes:
- Ver cambios individuales o de todos los archivos seleccionando **"Ver todos los cambios"** en el módulo de Chat
- Seleccioná **"Revertir todos los cambios"** para deshacer todas las modificaciones del agente
- Revertir a un [punto de control](https://kiro.dev/docs/chat/checkpoints) para restaurar archivos a un estado anterior localmente

---

## Comandos confiables

De forma predeterminada, Kiro requiere **aprobación antes de ejecutar cualquier comando**. Puede configurar una lista de comandos confiables en la configuración:

**Configuración → Buscar:** `Kiro Agent: Comandos confiables`

Kiro utiliza una coincidencia de prefijos de cadena simple:

| Patrón | Comportamiento |
|---|---|
| `instalación npm` | Coincidencia exacta: confía únicamente en este comando exacto |
| `npm *` | Comodín: confía en todos los comandos npm |
| `*` | Universal: confía en **todos** los comandos *(úselo con extrema precaución)* |

> ⚠️ El sistema trata los comandos completos como cadenas individuales y solo verifica si comienzan con patrones confiables. **No** analiza la estructura de comandos, cadenas o caracteres especiales. Configure patrones confiables con cuidado.

---

## Mejores prácticas

Las siguientes son pautas generales; no representan una solución de seguridad completa. Evalúe lo que es apropiado para su entorno.

### Protegiendo sus recursos

Al utilizar GitHub o la autenticación de Google con Kiro, tenga en cuenta que el agente de Kiro opera dentro de su entorno local y puede acceder a:
- Archivos y repositorios locales
- Variables de entorno
- Credenciales de AWS almacenadas en su entorno
- Otros archivos de configuración con información sensible

### Recomendaciones

**1. Aislamiento del Workspace**
- Mantenga los proyectos confidenciales en Workspaces separados
- Utilizá `.gitignore` (o `.kiroignore`) para evitar el acceso a archivos confidenciales
- Considere utilizar funciones de confianza del Workspace en su IDE

**2. Utilizá un entorno limpio**
- Considere la posibilidad de crear una cuenta de usuario dedicada o un entorno de contenedor para Kiro.
- Limite el acceso solo a los repositorios y recursos necesarios para su proyecto actual

**3. Administre las credenciales de AWS con cuidado**
- Utilizá credenciales temporales con los permisos adecuados
- Considere el uso de perfiles con nombre de AWS para aislar el acceso de Kiro
- Para trabajos confidenciales, elimine las credenciales de AWS de su entorno cuando no las necesite

**4. Control de acceso al repositorio**
- Al usar la autenticación de GitHub, revise a qué repositorios puede acceder Kiro
- Utilizá tokens de acceso específicos del repositorio cuando sea posible
- Auditar periódicamente los permisos de acceso.

---

## Seguridad de extensiones remotas

El soporte de extensiones remotas sigue el mismo modelo de seguridad que las extensiones locales. Cuando se utiliza desarrollo remoto (SSH, contenedores, WSL), las extensiones se ejecutan en el entorno remoto con los permisos del usuario remoto. Asegúrese de que los entornos remotos estén correctamente protegidos y que solo se instalen extensiones confiables.