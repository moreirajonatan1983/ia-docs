# Setup — Autonomous Agent

> **Source:** [kiro.dev/docs/autonomous-agent/setup/](https://kiro.dev/docs/autonomous-agent/setup/)
> **Estado:** Preview

---

Comenzá con el Kiro Autonomous Agent conectando tu cuenta de GitHub y configurando el acceso a tus repositorios.

---

## Prerequisites

- Una cuenta de Kiro activa
- Cuenta de GitHub con permisos de escritura en los repositorios que querés usar
- El Kiro Agent GitHub App instalado en tu organización o cuenta personal (lo hace un owner)

---

## Steps

### 1. Ir al Web App

Navegá a [app.kiro.dev/agent](https://app.kiro.dev/agent) para acceder al Autonomous Agent.

### 2. Iniciar sesión

Ingresá con tu cuenta de Kiro existente.

### 3. Vincular tu cuenta de GitHub

Conectá tu cuenta de GitHub para darle al agente acceso a tus repositorios:

1. Ir a **Settings** en el web app
2. Hacer clic en **"Connect GitHub"**
3. Autorizar la **Kiro Agent GitHub app**
4. Seleccionar a qué repositorios puede acceder el agente

> Necesitás tener **permisos de escritura** en los repositorios para que el agente pueda crear branches y abrir pull requests.

---

## How Repository Access Works

Kiro Autonomous Agent muestra todos los repositorios donde se cumplen **ambas condiciones**:

1. Tu usuario de GitHub tiene acceso al repositorio
2. El Kiro Agent GitHub app fue instalado y autorizado para ese repositorio

Esto significa que verás repositorios de cuentas personales, repositorios compartidos y organizaciones — siempre que tanto tu usuario de GitHub como la Kiro Agent app tengan acceso.

---

## Next Steps

Una vez que conectaste tu cuenta de GitHub, estás listo para [crear tu primera tarea →](../02_Using%20the%20agent/02_Creating%20tasks.md)

Ver también:
- [GitHub integration →](../04_GitHub.md)
- [Using the agent →](../02_Using%20the%20agent/)