# Integración de GitHub: agente autónomo

> **Fuente:** [kiro.dev/docs/autonomous-agent/github/](https://kiro.dev/docs/autonomous-agent/github/)

---

## Instalación

Conecta tu cuenta de GitHub al Agente Autónomo Kiro:

1. Navegá a [app.kiro.dev/agent](https://app.kiro.dev/agent) y ve a **Configuración**
2. Seleccioná **"Connect GitHub"** bajo Integraciones
3. Autorizá la **aplicación Kiro Agent GitHub**
4. Otorgá acceso a repositorios específicos o todos los repositorios de tu organización

> La aplicación Kiro Agent GitHub solo necesita instalarse **una vez por organización o cuenta**. Los propietarios de la organización seleccionan a qué repositorios pueden acceder la aplicación, controlando qué repositorios están disponibles para Kiro.

**Visibilidad de repositorios por usuario:** Cada usuario ve todos los repositorios donde se cumplen ambas condiciones:
1. La aplicación Kiro Agent GitHub fue instalada y autorizada para ese repositorio
2. La cuenta de GitHub del usuario tiene acceso a ese repositorio

Los usuarios solo pueden asignar tareas a repositorios donde tienen **permisos de escritura**. Otros usuarios no pueden asignar tareas en tu nombre.

---

## Asignación de tareas desde problemas de GitHub

Podés asignar trabajo directamente desde issues de GitHub de dos maneras:

**Con la etiqueta `kiro`:**  
Kiro comenzará a trabajar en la tarea y escuchará todos los comentarios del número para contexto o feedback adicional.

**Con el comando `/kiro` en un comentario:**  
Asigna ese tema específico a Kiro.

Si usas `/kiro` pero no registras tu cuenta de GitHub en Kiro, recibirás instrucciones para hacerlo. La aplicación Kiro Agent GitHub debe estar instalada en el repositorio.

---

## Cómo funciona el agente con GitHub

**Repositorios de clones**  
El agente clona repositorios autorizados en su entorno sandbox aislado. Puede trabajar en múltiples repositorios en una sola tarea, manteniendo contexto y coordinando cambios.

**Crea ramas y commits**  
Para cada tarea, el agente:
- Crea una rama característica desde tu rama predeterminada
- Hace commits con mensajes claros
- Pushea al repositorio
- Actúa en tu nombre e incluye tanto a vos como a él mismo como coautores en cada compromiso

**Abre y actualiza las pull requests**  
Después de completar el trabajo, se abren pull request con una descripción detallada de los cambios, el enfoque de implementación y las compensaciones consideradas.

> El agente **solo responde a tu feedback explícito e instrucciones** (el usuario que creó la tarea). Nunca combine cambios automáticamente.

---

## Abordar los comentarios de Pull Requests

Kiro proporciona dos comandos para manejar comentarios de pull request:

| comando | Descripción |
|---|---|
| `/kiro todos` | Aborda todos los comentarios de todos los revisores en todo el PR. Ideal para manejar todo el feedback a la vez. |
| `/kiro arreglar` | Aborda todos los comentarios dentro de un hilo de conversación específico. Ideal para focalizarse en un tema a la vez. |

Para prevenir que un comentario sea abordado, elimínelo o respondé con su propia perspectiva antes de usar un comando.

También podés dar comentarios desde la vista de tareas en [app.kiro.dev/agent](https://app.kiro.dev/agent).

**Comentarios de acciones de GitHub** (verificaciones automatizadas, pruebas, análisis de seguridad) se aborda automáticamente cuando hay cualquier comentario.

### Enseñar al agente mediante revisiones de código

Podés enseñarle al agente los patrones de tu equipo a través del feedback en PRs. Cuando dejás comentarios como "recordá usar nuestro manejo estándar de errores" o "siempre sigue nuestras convenciones de naming", el agente aprende y esos aplicaciones patrones en trabajos futuros en todos tus repositorios.

> Solo **tu feedback** influye en el aprendizaje del agente. Los comentarios de otros revisores no afectan lo que aprende.

---

## Múltiples usuarios en el mismo repositorio

Cuando varios miembros del equipo tienen el Agente Autónomo conectado al mismo repositorio, cada usuario puede asignar tareas de forma independiente.

**Cómo funciona:**
- La aplicación Kiro Agent GitHub solo necesita instalarse una vez por repositorio
- Cada usuario registrado puede asignar tareas de forma independiente
- Si Múltiples usuarios asignan el mismo número de GitHub (usando la etiqueta `kiro` o el comando `/kiro`), Kiro crea tareas separadas para cada usuario
- Cada tarea se corre independientemente en su propio sandbox aislado

**Mejores prácticas:**
- Coordinará con tu equipo para evitar trabajo duplicado en el mismo tema.
- Usaremos la función de asignación de issues de GitHub para indicar quién está trabajando en qué
- Revisá los pull request abiertos antes de asignar tareas similares para evitar conflictos

---

## Permisos

### Instalación y configuración de la aplicación

La aplicación Kiro Agent GitHub se instala una vez por organización o cuenta por un propietario. La configuración de la aplicación es global y define el conjunto máximo de repositorios a los que Kiro puede acceder.

### Acceso a nivel de repositorio

Cada usuario solo puede trabajar con repositorios donde se cumplen ambas condiciones:
- La aplicación Kiro Agent GitHub tiene acceso otorgado por un propietario de la organización
- El usuario tiene permisos de escritura en el repositorio

### Se requieren permisos de repositorio

**Leer y escribir:**
- Acciones: flujos de trabajo, ejecuciones de flujos de trabajo y artefactos
- Cheques — Cheques sobre el código
- Contenidos — Contenidos del repositorio, commits, Branches, Releases y merges
- Issues — Issues y comentarios relacionados, asignados, etiquetas e hitos
- Pull requests: Pull Requests y comentarios relacionados, asignados, etiquetas, hitos y fusiones
- Flujos de trabajo — Actualizar archivos de flujo de trabajo de GitHub Action

**Solo lectura:**
- Metadatos — Buscar repositorios, listar colaboradores (obligatorio)
- Administración — Configuración del repositorio, equipos y colaboradores
- Confirmar estados

**Permisos de organización (solo lectura):**
- Administración — Gestionar acceso a la organización

### Eventos de webhook

La aplicación se suscribe a: pull requests, revisiones de pull requests, comentarios de revisión de pull requests, problemas, comentarios de problemas, eventos de inserción, creación/eliminación de ramas/etiquetas, lanzamientos, cambios en el repositorio, ejecuciones de flujo de trabajo, y otros.

### Revocación

- **Propietarios de la organización** pueden revocar el acceso del agente en cualquier momento removiendo permisos de repositorios de la aplicación Kiro Agent GitHub (bloquea el acceso para todos los usuarios)
- **Usuarios individuales** pueden desconectar su cuenta de GitHub de Kiro en cualquier momento, lo que detiene su agente de acceso a cualquier repositorio

### Protección de sucursales

El agente respeta tus reglas de protección de sucursal. No puedes pushear directamente a sucursales protegidas y debes pasar por tu flujo de trabajo estándar de pull request.

---

## Relacionado

- [Configuración →](../01_Get%20started/01_Setup.md)
- [Creando tareas →](../02_Using%20the%20agent/02_Creating%20tasks.md)
- [Protección de datos →](./05_Data%20protection.md)