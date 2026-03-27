# GitHub Integration — Autonomous Agent

> **Source:** [kiro.dev/docs/autonomous-agent/github/](https://kiro.dev/docs/autonomous-agent/github/)

---

## Installation

Conectá tu cuenta de GitHub al Kiro Autonomous Agent:

1. Navegá a [app.kiro.dev/agent](https://app.kiro.dev/agent) y ve a **Settings**
2. Seleccioná **"Connect GitHub"** bajo Integrations
3. Autorizá la **Kiro Agent GitHub app**
4. Otorgá acceso a repositorios específicos o todos los repositorios de tu organización

> El Kiro Agent GitHub app solo necesita instalarse **una vez por organización o cuenta**. Los owners de la organización seleccionan a qué repositorios puede acceder la app, controlando qué repositorios están disponibles para Kiro.

**Visibilidad de repos por usuario:** Cada usuario ve todos los repositorios donde se cumplen ambas condiciones:
1. El Kiro Agent GitHub app fue instalado y autorizado para ese repositorio
2. La cuenta de GitHub del usuario tiene acceso a ese repositorio

Los usuarios solo pueden asignar tareas a repositorios donde tienen **permisos de escritura**. Otros usuarios no pueden asignar tareas en tu nombre.

---

## Assigning Tasks from GitHub Issues

Podés asignar trabajo directamente desde issues de GitHub de dos maneras:

**Con el label `kiro`:**  
Kiro comenzará a trabajar en la tarea y escuchará todos los comentarios del issue para contexto o feedback adicional.

**Con el comando `/kiro` en un comentario:**  
Asigna ese issue específico a Kiro.

Si usás `/kiro` pero no registraste tu cuenta de GitHub en Kiro, recibirás instrucciones para hacerlo. El Kiro Agent GitHub app debe estar instalado en el repositorio.

---

## How the Agent Works with GitHub

**Clona repositorios**  
El agente clona repositorios autorizados en su entorno sandbox aislado. Puede trabajar en múltiples repositorios en una sola tarea, manteniendo contexto y coordinando cambios.

**Crea branches y commits**  
Para cada tarea, el agente:
- Crea un feature branch desde tu default branch
- Hace commits con mensajes claros
- Pushea al repositorio
- Actúa en tu nombre e incluye tanto a vos como a él mismo como co-autores en cada commit

**Abre y actualiza pull requests**  
Después de completar el trabajo, abre pull requests con una descripción detallada de los cambios, el enfoque de implementación y los trade-offs considerados.

> El agente **solo responde a tu feedback explícito e instrucciones** (el usuario que creó la tarea). Nunca mergea cambios automáticamente.

---

## Addressing PR Feedback

Kiro provee dos comandos para manejar comentarios de pull request:

| Comando | Descripción |
|---|---|
| `/kiro all` | Aborda todos los comentarios de todos los reviewers en todo el PR. Ideal para manejar todo el feedback a la vez. |
| `/kiro fix` | Aborda todos los comentarios dentro de un thread de conversación específico. Ideal para focalizarse en un tema a la vez. |

Para prevenir que un comentario sea abordado, eliminalo o respondé con tu propia perspectiva antes de usar un comando.

También podés dar feedback desde la vista de tareas en [app.kiro.dev/agent](https://app.kiro.dev/agent).

**GitHub Action feedback** (automated checks, tests, security scans) se aborda automáticamente cuando dás cualquier feedback.

### Teaching the Agent Through Code Reviews

Podés enseñarle al agente los patrones de tu equipo a través del feedback en PRs. Cuando dejás comentarios como "recordá usar nuestro manejo estándar de errores" o "siempre seguí nuestras convenciones de naming", el agente aprende y aplica esos patrones en trabajos futuros en todos tus repositorios.

> Solo **tu feedback** influye en el aprendizaje del agente. Los comentarios de otros reviewers no afectan lo que aprende.

---

## Multiple Users on the Same Repository

Cuando múltiples miembros del equipo tienen el Autonomous Agent conectado al mismo repositorio, cada usuario puede asignar tareas de forma independiente.

**Cómo funciona:**
- El Kiro Agent GitHub app solo necesita instalarse una vez por repositorio
- Cada usuario registrado puede asignar tareas independientemente
- Si múltiples usuarios asignan el mismo issue de GitHub (usando el label `kiro` o el comando `/kiro`), Kiro crea tareas separadas para cada usuario
- Cada tarea corre independientemente en su propio sandbox aislado

**Best practices:**
- Coordiná con tu equipo para evitar trabajo duplicado en el mismo issue
- Usá la feature de asignación de issues de GitHub para indicar quién está trabajando en qué
- Revisá los pull requests abiertos antes de asignar tareas similares para evitar conflictos

---

## Permissions

### App Installation and Configuration

El Kiro Agent GitHub app se instala una vez por organización o cuenta por un owner. La configuración de la app es global y define el conjunto máximo de repositorios a los que Kiro puede acceder.

### Repository-Level Access

Cada usuario solo puede trabajar con repositorios donde se cumplen ambas condiciones:
- El Kiro Agent GitHub app tiene acceso otorgado por un owner de la organización
- El usuario tiene permisos de escritura en el repositorio

### Repository Permissions Required

**Read & Write:**
- Actions — Workflows, workflow runs y artifacts
- Checks — Checks sobre el código
- Contents — Contenidos del repositorio, commits, branches, releases y merges
- Issues — Issues y comentarios relacionados, assignees, labels y milestones
- Pull requests — PRs y comentarios relacionados, assignees, labels, milestones y merges
- Workflows — Actualizar archivos de GitHub Action workflow

**Read-only:**
- Metadata — Buscar repositorios, listar colaboradores (obligatorio)
- Administration — Settings del repositorio, teams y colaboradores
- Commit statuses

**Organization permissions (Read-only):**
- Administration — Gestionar acceso a la organización

### Webhook Events

La app se suscribe a: pull requests, pull request reviews, pull request review comments, issues, issue comments, push events, branch/tag creation/deletion, releases, repository changes, workflow runs, y otros.

### Revocation

- **Organization owners** pueden revocar el acceso del agente en cualquier momento removiendo permisos de repositorios de la Kiro Agent GitHub app (bloquea el acceso para todos los usuarios)
- **Usuarios individuales** pueden desconectar su cuenta de GitHub de Kiro en cualquier momento, lo que detiene su agente de acceder a cualquier repositorio

### Branch Protection

El agente respeta tus reglas de protección de branch. No puede pushear directamente a branches protegidos y debe pasar por tu workflow estándar de pull requests.

---

## Related

- [Setup →](../01_Get%20started/01_Setup.md)
- [Creating tasks →](../02_Using%20the%20agent/02_Creating%20tasks.md)
- [Data protection →](./05_Data%20protection.md)