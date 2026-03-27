# Configuración: Agente autónomo

> **Fuente:** [kiro.dev/docs/autonomous-agent/setup/](https://kiro.dev/docs/autonomous-agent/setup/)
> **Estado:** Vista previa

---

Comenzá con el Kiro Autónomo Agente conectando tu cuenta de GitHub y configurando el acceso a tus repositorios.

---

## Requisitos previos

- Una cuenta de Kiro activa
- Cuenta de GitHub con permisos de escritura en los repositorios que quieres usar
- La aplicación Kiro Agent GitHub instalada en tu organización o cuenta personal (lo hace un propietario)

---

## Pasos

### 1. Aplicación web Ir al

Navegá a [app.kiro.dev/agent](https://app.kiro.dev/agent) para acceder al Agente Autónomo.

### 2. Iniciar sesión

Ingresá con tu cuenta de Kiro existente.

### 3. Vincular tu cuenta de GitHub

Conecta tu cuenta de GitHub para darle al agente acceso a tus repositorios:

1. Vaya a **Configuración** en la aplicación web
2. Hacer clic en **"Conectar GitHub"**
3. Autorizar la **aplicación Kiro Agent GitHub**
4. Seleccione a qué repositorios puede acceder el agente

> Necesitás tener **permisos de escritura** en los repositorios para que el agente pueda crear sucursales y abrir pull request.

---

## Cómo funciona el acceso al repositorio

Kiro Autónomo Agente muestra todos los repositorios donde se cumplen **ambas condiciones**:

1. Tu usuario de GitHub tiene acceso al repositorio
2. La aplicación Kiro Agent GitHub fue instalada y autorizada para ese repositorio

Esto significa que verás repositorios de cuentas personales, repositorios compartidos y organizaciones — siempre que tanto tu usuario de GitHub como la aplicación Kiro Agent tengan acceso.

---

## Próximos pasos

Una vez que conectaste tu cuenta de GitHub, estás listo para [crear tu primera tarea →](../02_Using%20the%20agent/02_Creating%20tasks.md)

Ver también:
- [Integración de GitHub →](../04_GitHub.md)
- [Usando el agente →](../02_Usando%20the%20agent/)