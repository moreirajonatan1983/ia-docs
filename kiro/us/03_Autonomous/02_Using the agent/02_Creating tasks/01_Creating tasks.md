# Creating Tasks

> **Source:** [kiro.dev/docs/autonomous-agent/using-the-agent/creating-tasks/](https://kiro.dev/docs/autonomous-agent/using-the-agent/creating-tasks/)

---

## From app.kiro.dev/agent

Navegá a [app.kiro.dev/agent](https://app.kiro.dev/agent) para iniciar un nuevo chat:

1. Opcionalmente, seleccioná múltiples repositorios al iniciar el chat
2. Describí lo que querés que haga el agente
3. Si no seleccionaste repositorios al inicio, se te pedirá que los elijas cuando le pidas al agente que trabaje en algo

El agente analiza tu request, desglosa el trabajo y comienza la ejecución.

> **Multi-repo tasks:** El Kiro Autonomous Agent puede trabajar en múltiples repositorios en una sola tarea. Cuando asignás trabajo que abarca múltiples repos, coordina todos los cambios y abre pull requests en cada uno. Solo seleccioná repositorios de confianza, especialmente al mezclar repos públicos y privados, ya que el agente aprende y sigue instrucciones en el código del repositorio — incluso si son maliciosas.

---

## From GitHub Issues

Necesitás [conectar GitHub →](../04_GitHub.md) primero.

**Usando el comando `/kiro`:**  
Mencioná `/kiro` en un comentario de cualquier issue para asignarle esa tarea al Kiro Autonomous Agent.

**Usando el label `kiro`:**  
Agregá el label `kiro` a cualquier issue. El Kiro Autonomous Agent comenzará a trabajar en la tarea y escuchará todos los comentarios del issue para contexto o feedback adicional.

---

## Task Lifecycle

Las tareas pasan por diferentes estados mientras el agente trabaja:

| Estado | Descripción |
|---|---|
| **Queued** | La tarea está esperando para iniciar. Ocurre cuando alcanzaste el límite de 10 tareas concurrentes. |
| **In progress** | El agente está trabajando activamente — analizando requisitos, escribiendo código o ejecutando tests. |
| **Needs attention** | La tarea necesita input o el agente tiene una pregunta de aclaración. Revisá el mensaje del agente y proporcioná la información solicitada. |
| **Completed** | El agente terminó el trabajo y abrió pull requests. Revisá los cambios y proporcioná feedback. Dar feedback mueve la tarea a *queued* y luego a *in progress* cuando hay un slot disponible. |
| **Cancelled** | La tarea fue cancelada y no se completará. Las tareas canceladas no pueden reanudarse. |

---

## Task Tips

Seguí estas best practices al crear tareas:

**Sé específico sobre el resultado**  
Describí claramente cómo querés que se vea el resultado final. En lugar de "mejorar el login flow", decí "agregar funcionalidad de reseteo de contraseña en la página de login con verificación por email."

**Describí el problema que estás tratando de resolver**  
Explicá el contexto y por qué se necesita el trabajo. Esto ayuda al agente a entender restricciones y tomar mejores decisiones de implementación.

**Proporcioná contexto relevante**  
Linkeá documentación relacionada, ejemplos, o código existente que deba informar la implementación.

**Definí criterios de aceptación**  
Listá condiciones específicas que deben cumplirse para que la tarea se considere completa.

**Usá steering files**  
El Kiro Autonomous Agent busca automáticamente steering files en la carpeta `.kiro/steering/` en la raíz de tu repositorio. Estos archivos Markdown definen los estándares, arquitectura y convenciones de tu equipo, asegurando que el agente siga consistentemente tus patrones establecidos. Son especialmente útiles para:
- Convenciones de código
- Patrones arquitectónicos
- Preferencias del stack tecnológico
- Enfoques de testing

---

## Related

- [Chatting with the agent →](./01_Chatting%20with%20the%20agent.md)
- [Agent Sandbox →](../03_Agent%20Sandbox/)
- [GitHub integration →](../04_GitHub.md)