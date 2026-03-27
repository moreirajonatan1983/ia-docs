#Chat — Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/chat/](https://kiro.dev/docs/cli/chat/)

---

## Iniciar una sesión

```bash
kiro-cli
```

O inicie un chat con un agente específico:
```golpecito
kiro-cli --agente myagent
```

---

## Ingresar estados de cuenta de varias líneas

Para ingresar declaraciones de varias líneas, use el comando `/editor` o presione `Ctrl(^) + J` para insertar una nueva línea.

El comando `/editor` abre su editor predeterminado (el predeterminado es `vi`) donde puede redactar mensajes más largos y de varias líneas. Después de guardar y cerrar el editor, el contenido se envía como mensaje a Kiro.

También puede usar el comando `/reply` para abrir su editor con el mensaje del asistente más reciente citado para responder, lo cual es útil para respuestas de varias líneas a mensajes anteriores.

---

## Persistencia de la conversación

Kiro recuerda tus conversaciones según la carpeta donde las iniciaste. Cuando inicias una sesión en un directorio donde previamente conversaste con Kiro, puedes decirle a Kiro que cargue automáticamente ese historial de conversaciones.

### Persistencia basada en directorios

Reanudar una conversación en el directorio actual:
```golpecito
chat kiro-cli --reanudar
```

Abra un selector de sesiones interactivo para elegir entre sesiones anteriores:
```golpecito
chat kiro-cli --resume-selector
```

### Iniciar una nueva conversación

Utilice el comando `/chat new` sin reiniciar la CLI. Esto guarda su sesión actual en la base de datos y comienza una nueva:

```golpecito
# Iniciar una nueva conversación
/chatear nuevo

# Inicie una nueva conversación con un mensaje inicial
/chat nuevo ¿Cómo configuro un proyecto de React?
```

Utilice `/chat resume` para volver a cualquier sesión anterior.

### Guardar y cargar conversaciones manualmente

Mientras estás en una sesión de chat:

```golpecito
# Guardar la conversación actual en un archivo JSON
/guardar chat ./mi-conversación-de-proyecto
/chat save ./mi-proyecto-conversación -f # sobrescribir existente
/guardar chat /home/usuario/proyecto/mi-proyecto-conversación.json

# Cargar una conversación desde un archivo JSON previamente guardado
/carga de chat ./mi-proyecto-conversación.json
```

> Nota: No puede utilizar `~` para indicar su directorio de inicio en la ruta. Los comandos `/chat save` y `/chat load` operan independientemente del directorio donde se creó originalmente la conversación.