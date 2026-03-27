# Creando tareas

> **Fuente:** [kiro.dev/docs/autonomous-agent/using-the-agent/creating-tasks/](https://kiro.dev/docs/autonomous-agent/using-the-agent/creating-tasks/)

---

## Desde app.kiro.dev/agent

Navegá a [app.kiro.dev/agent](https://app.kiro.dev/agent) para iniciar un nuevo chat:

1. Opcionalmente, seleccione múltiples repositorios al iniciar el chat
2. Describí lo que querés que haga el agente
3. Si no seleccionaste repositorios al inicio, se te pedirá que los elijas cuando le pidas al agente que trabaje en algo

El agente analiza tu solicitud, desglosa el trabajo y comienza la ejecución.

> **Tareas de múltiples repositorios:** El Kiro Autónomo Agente puede trabajar en múltiples repositorios en una sola tarea. Cuando asignas trabajo que abarca múltiples repositorios, coordina todos los cambios y abre pull request en cada uno. Solo seleccioná repositorios de confianza, especialmente al mezclar repositorios públicos y privados, ya que el agente aprende y sigue instrucciones en el código del repositorio — incluso si son maliciosas.

---

## De problemas de GitHub

Necesitás [conectar GitHub →](../04_GitHub.md) primero.

**Usando el comando `/kiro`:**  
Mencioná `/kiro` en un comentario de cualquier asunto para asignarle esa tarea al Agente Autónomo Kiro.

**Usando la etiqueta `kiro`:**  
Agrega el label `kiro` a cualquier tema. El Kiro Autónomo Agente comenzará a trabajar en la tarea y escuchará todos los comentarios del problema para contexto o feedback adicional.

---

## Ciclo de vida de la tarea

Las tareas pasan por diferentes estados mientras el agente trabaja:

| Estado | Descripción |
|---|---|
| **En cola** | La tarea está esperando para iniciar. Ocurre cuando alcanzaste el límite de 10 tareas concurrentes. |
| **En progreso** | El agente está trabajando activamente — analizando requisitos, escribiendo código o ejecutando pruebas. |
| **Necesita atención** | La tarea necesita entrada o el agente tiene una pregunta de aclaración. Revise el mensaje del agente y proporcione la información solicitada. |
| **Completado** | El agente terminó el trabajo y abrió pull request. Revisará los cambios y proporcionará comentarios. Dar feedback mueve la tarea a *en cola* y luego a *en progreso* cuando hay un espacio disponible. |
| **Cancelado** | La tarea fue cancelada y no se completará. Las tareas canceladas no pueden reanudarse. |

---

## Consejos para tareas

Siga estas mejores prácticas al crear tareas:

**Sé específico sobre el resultado**  
Describí claramente cómo querés que se vea el resultado final. En lugar de "mejorar el flujo de inicio de sesión", decí "agregar funcionalidad de restablecimiento de contraseña en la página de inicio de sesión con verificación por correo electrónico".

**Describe el problema que estás tratando de resolver**  
Explique el contexto y por qué se necesita el trabajo. Esto ayuda al agente a entender las restricciones y tomar mejores decisiones de implementación.

**Proporcioná contexto relevante**  
Linkeá documentación relacionada, ejemplos, o código existente que deba informar la implementación.

**Definición de criterios de aceptación**  
Lista de condiciones específicas que deben cumplirse para que la tarea se considere completa.

**Usá archivos de dirección**  
El Kiro Self Agent busca automáticamente archivos de dirección en la carpeta `.kiro/steering/` en la raíz de tu repositorio. Estos archivos Markdown definen los estándares, arquitectura y convenciones de tu equipo, asegurando que el agente siga consistentemente tus patrones establecidos. Son especialmente útiles para:
- Convenciones de código
- Patrones arquitectónicos
- Preferencias del stack tecnológico
- Enfoques de prueba

---

## Relacionado

- [Chateando con el agente →](./01_Chatting%20with%20the%20agent.md)
- [Agente Sandbox →](../03_Agent%20Sandbox/)
- [Integración de GitHub →](../04_GitHub.md)