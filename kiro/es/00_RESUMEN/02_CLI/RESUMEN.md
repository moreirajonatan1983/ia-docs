# Manual Consolidado: Kiro CLI

> Este documento es una consolidación extensa y detallada de toda la documentación referida a esta herramienta.



---

*📂 Capítulo: **Get started > Installation***

## Instalación: Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/installation/](https://kiro.dev/docs/cli/installation/)

---

###macOS

Puede instalar Kiro CLI para macOS de forma nativa en la línea de comando:

```bash
curl -fsSL https://cli.kiro.dev/install | bash
```

Kiro le indicará que abra su navegador web, donde seguirá los pasos que se indican en [Autenticación](https://kiro.dev/docs/cli/authentication).

---

### Linux — Imagen de aplicación

Puede instalar Kiro CLI para Linux utilizando el formato AppImage, que es portátil y funciona en la mayoría de las distribuciones de Linux sin necesidad de instalación.

1. Descargue Kiro CLI para Linux AppImage:
   ```
   https://desktop-release.q.us-east-1.amazonaws.com/latest/kiro-cli.appimage
   ```

2. Haga que AppImage sea ejecutable:
   ```golpecito
   chmod +x kiro-cli.appimage
   ```

3. Ejecute AppImage:
   ```golpecito
   ./kiro-cli.appimage
   ```

4. Kiro le indicará que abra su navegador web para seguir los pasos de [Autenticación](https://kiro.dev/docs/cli/authentication).

---

### Linux: con un archivo zip

#### Requisitos de instalación y actualización

- Debes poder extraer o "descomprimir" el paquete descargado.
- Kiro CLI requiere **glibc 2.34 o posterior** (incluido de forma predeterminada en la mayoría de las principales distribuciones de Linux lanzadas desde 2021).
- Para distribuciones más antiguas con glibc < 2.34, utilice la **versión especial basada en musl** (indicada por `-musl.zip` en el nombre del archivo).
- Compatible con versiones **x86_64** de 64 bits** y **ARM aarch64** de: Fedora, Ubuntu, Amazon Linux 2023.

#### Comprobando tu versión de glibc

```bash
ldd --version
```

- Si **2.34 o más reciente** → use la versión estándar.
- Si es **mayor** → use la versión musl.

#### Descargue el archivo de instalación

**Versión estándar (glibc 2.34+):**

Linuxx86-64:
```golpecito
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-x86_64-linux.zip' \
  -o 'kirocli.zip'
```

BRAZO de Linux (aarch64):
```golpecito
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-aarch64-linux.zip' \
  -o 'kirocli.zip'
```

**Versión Musl (para glibc < 2.34):**

Linux x86-64 con musl:
```golpecito
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-x86_64-linux-musl.zip' \
  -o 'kirocli.zip'
```

Linux ARM (aarch64) con musl:
```golpecito
curl --proto '=https' --tlsv1.2 -sSf \
  'https://desktop-release.q.us-east-1.amazonaws.com/latest/kirocli-aarch64-linux-musl.zip' \
  -o 'kirocli.zip'
```

#### Instalar Kiro CLI

1. Descomprima el instalador:
   ```golpecito
   descomprimir kirocli.zip
   ```

2. Ejecute el programa de instalación:
   ```golpecito
   ./kirocli/install.sh
   ```

De forma predeterminada, los archivos se instalan en `~/.local/bin`.

---

### Linux — Ubuntu (paquete .deb)

1. Descargue Kiro CLI para Ubuntu:
   ```golpecito
   wget https://desktop-release.q.us-east-1.amazonaws.com/latest/kiro-cli.deb
   ```

2. Instale el paquete:
   ```golpecito
   sudo dpkg -i kiro-cli.deb
   sudo apt-get install -f
   ```

3. Inicie Kiro CLI:
   ```golpecito
   kiro-cli
   ```

4. Kiro le indicará que abra su navegador web para seguir los pasos de [Autenticación](https://kiro.dev/docs/cli/authentication).

---

### Configuración de proxy

Kiro CLI (v1.8.0 y posteriores) admite servidores proxy comúnmente utilizados en entornos empresariales. La CLI respeta automáticamente las variables de entorno de proxy estándar.

#### Configuración de variables de entorno de proxy

```golpecito
## Proxy HTTP para tráfico no SSL
exportar HTTP_PROXY=http://proxy.company.com:8080

## Proxy HTTPS para tráfico SSL
exportar HTTPS_PROXY=http://proxy.company.com:8080

## Omitir proxy para dominios específicos
exportar NO_PROXY=localhost,127.0.0.1,.empresa.com
```

#### Proxy con autenticación

```bash
export HTTP_PROXY=http://username:password@proxy.company.com:8080
export HTTPS_PROXY=http://username:password@proxy.company.com:8080
```

#### Solución de problemas de proxy

- Verificar la accesibilidad y las credenciales del servidor proxy.
- Asegúrese de que su firewall corporativo permita conexiones a puntos finales de AWS
- Póngase en contacto con su administrador de TI si falla la validación del certificado SSL
- Verifique que el servidor proxy admita los protocolos requeridos

---

### Desinstalación de Kiro CLI

**macOS:**
```golpecito
desinstalación de kiro-cli
```

**Ubuntu:**
```golpecito
sudo apt-get eliminar kiro-cli
sudo apt-get purge kiro-cli # Eliminar los archivos de configuración restantes
```

---

### Depuración de Kiro CLI

Si tiene problemas con Kiro CLI, ejecute `kiro-cli doctor` para identificar y solucionar problemas comunes:

```bash
kiro-cli doctor
```

---

### Próximos pasos

- [Autenticación →](https://kiro.dev/docs/cli/authentication/)
- [Modelos →](https://kiro.dev/docs/cli/models/)

---

*📂 Capítulo: **Get started > Authentication***

## Métodos de autenticación: Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/authentication/](https://kiro.dev/docs/cli/authentication/)

---

### Iniciar sesión en Kiro CLI

1. En la línea de comando, ingrese `kiro-cli` o `kiro-cli login`. Se le pedirá que presione Entrar para completar el inicio de sesión en su navegador.

2. En su navegador, elija la organización o sistema a través del cual se autenticará:
   -Google
   -GitHub
   - Identificación del constructor
   - Su organización, incluido AWS GovCloud (EE. UU.)

3. Después de autenticarse, recibirá un mensaje en su navegador que lo dirigirá nuevamente a su terminal.

4. Cuando regrese a su terminal, deberá iniciar sesión con Kiro CLI.

> **Nota:** Los métodos de inicio de sesión individuales como GitHub, Google y AWS Builder ID **no están disponibles** en las regiones de AWS GovCloud (EE. UU.).
>
> Los usuarios saben que usarán Kiro con AWS GovCloud (EE. UU.) asegurándose de que la URL de inicio utilizada durante la autenticación contenga `"us-gov-home"`, por ejemplo:
> ```
> https://start.us-gov-home.awsapps.com/directory/d-XXXXXXXXXX
> ```
>
> **Kiro IDE versión 0.9.2+** y **Kiro CLI versión 1.25.0+** son necesarios para la compatibilidad con las regiones de AWS GovCloud (EE. UU.).

---

### Iniciar sesión desde una máquina remota

Cuando se ejecuta Kiro CLI en una máquina remota (a través de SSH, SSM, contenedores, etc.), la autenticación funciona de manera diferente ya que la máquina remota no puede abrir un navegador.

- **Para Builder ID e IAM Identity Center:** Kiro CLI utiliza **autenticación de código de dispositivo**. Verá una URL y un código para ingresar en su navegador local; no se requiere configuración adicional.
- **Para inicio de sesión social (Google o GitHub):** La CLI utiliza autenticación PKCE que requiere **reenvío de puertos**. La devolución de llamada de OAuth redirige a "localhost", que no llegará a la CLI remota sin un túnel.

**Para iniciar sesión con inicio de sesión social en una máquina remota:**

1. Ejecute `kiro-cli login` y seleccione *"Usar gratis con Google o GitHub"*
2. Anote el número de puerto que se muestra (varía cada vez, por ejemplo, `49153`)
3. En una nueva terminal en su **máquina local**, configure el reenvío de puertos:
   ```golpecito
   ssh -L <PUERTO>:localhost:<PUERTO> -N usuario@host-remoto
   ```
   Reemplace `<PORT>` con el puerto del paso 2 y `user@remote-host` con sus credenciales remotas.
4. Presione Entrar en la CLI y luego abra la URL en su navegador local.
5. Autenticación completa: la devolución de llamada llega a la CLI a través del túnel

**Ejemplos de reenvío de puertos SSH:**

```golpecito
## Reenvío de puerto básico (reemplace 49153 con su puerto real)
ssh -L 49153:localhost:49153 -N usuario@host-remoto

## Con un archivo de identidad personalizado (común para EC2)
ssh -i ~/.ssh/my-key.pem -L 49153:localhost:49153 -N usuario@host-remoto

## Usando un alias de configuración SSH
ssh -L 49153:localhost:49153 -N miservidor
```

**Solución de problemas de reenvío de puertos:**

| Problema | Solución |
|---|---|
| Se agotó el tiempo de autenticación | El reenvío de puertos no está activo o es un puerto incorrecto. Verifique que el puerto coincida con la salida CLI. |
| No se pudo vincular el puerto de devolución de llamada | El puerto está en uso en el control remoto. Ejecute `lsof -i :<PORT>` para identificar el proceso. |
| Dirección ya en uso (SSH) | El puerto está en uso local. Cierre otros túneles o sesiones SSH obsoletas. |
| El túnel se desconecta a mitad de la autenticación | Mantenga la terminal SSH abierta hasta que se complete la autenticación. Agregue `-o ServerAliveInterval=60` |

---

### Cerrar sesión en Kiro CLI

```bash
kiro-cli logout
```

---

### Solución de problemas de autenticación

Si encuentra problemas durante el proceso de autenticación, como fallas de redireccionamiento del navegador o errores de inicio de sesión, consulte nuestra [guía de solución de problemas](https://kiro.dev/docs/troubleshooting/#authentication-issues) para obtener soluciones específicas de la plataforma y correcciones comunes.

---

### Próximos pasos

- [Revisar preguntas frecuentes →](https://kiro.dev/faq)
- [Explorar funciones de chat →](https://kiro.dev/docs/cli/chat)
- [Comenzar con Kiro CLI →](https://kiro.dev/docs/cli)

---

*📂 Capítulo: **Models***

## Modelos — Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/models/](https://kiro.dev/docs/cli/models/)

---

Kiro CLI admite los mismos modelos que el IDE. Consulte la [página de modelos IDE] (../../01_IDE/02_Models.md) para obtener los detalles completos del modelo, la tabla de comparación, las diferencias de comportamiento y las mejores prácticas.

---

### Comparación rápida

El costo es relativo a **Automático (1,0 veces el valor de referencia)**. Por ejemplo, una tarea que cuesta 10 créditos en Auto costaría 22 créditos en Opus, 4 créditos en Haiku o 0,5 créditos en Qwen3 Coder Next.

| Modelo | Mejor para | Costo |
|---|---|---|
| **Automático** *(recomendado)* | Uso general, mejor relación calidad/coste | 1,0x |
| **Claude Opus 4.6** | Codificación agente compleja, grandes bases de código | ~2,2x |
| **Claude Sonnet 4.6** | Flujos de trabajo de desarrollo iterativos, canalizaciones multimodelo | ~1,0x |
| **Claude Haiku 4.5** | Iteraciones rápidas, conservación del crédito | ~0,4x |
| **MiniMax M2.5** | Ciclo de vida de desarrollo completo a bajo costo | 0,25x |
| **DeepSeek 3.2** | Flujos de trabajo agentes, generación de código | 0,25x |
| **MiniMax M2.1** | Programación multilingüe, generación de UI | 0,15x |
| **Qwen3 Coder Siguiente** | — | 0,5x |

---

### Cómo cambiar de modelo

#### Desde la interfaz de chat

Utilice el menú desplegable de modelos en la interfaz de chat. Si no aparece un modelo, reinicie el cliente.

#### Desde la línea de comando

Establecer un modelo específico como predeterminado:
```golpecito
configuración de kiro-cli chat.defaultModel claude-opus4.6
```

Guarde el modelo **actual** como predeterminado para todas las sesiones futuras (desde una sesión de chat):
```
> /modelo establecido-actual-como-predeterminado
```

Esto almacena su preferencia en `~/.kiro/settings/cli.json`. Las nuevas sesiones utilizan automáticamente este modelo.

---

*📂 Capítulo: **Chat > Session management***

##Chat — Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/chat/](https://kiro.dev/docs/cli/chat/)

---

### Iniciar una sesión

```bash
kiro-cli
```

O inicie un chat con un agente específico:
```golpecito
kiro-cli --agente myagent
```

---

### Ingresar estados de cuenta de varias líneas

Para ingresar declaraciones de varias líneas, use el comando `/editor` o presione `Ctrl(^) + J` para insertar una nueva línea.

El comando `/editor` abre su editor predeterminado (el predeterminado es `vi`) donde puede redactar mensajes más largos y de varias líneas. Después de guardar y cerrar el editor, el contenido se envía como mensaje a Kiro.

También puede usar el comando `/reply` para abrir su editor con el mensaje del asistente más reciente citado para responder, lo cual es útil para respuestas de varias líneas a mensajes anteriores.

---

### Persistencia de la conversación

Kiro recuerda tus conversaciones según la carpeta donde las iniciaste. Cuando inicias una sesión en un directorio donde previamente conversaste con Kiro, puedes decirle a Kiro que cargue automáticamente ese historial de conversaciones.

#### Persistencia basada en directorios

Reanudar una conversación en el directorio actual:
```golpecito
chat kiro-cli --reanudar
```

Abra un selector de sesiones interactivo para elegir entre sesiones anteriores:
```golpecito
chat kiro-cli --resume-selector
```

#### Iniciar una nueva conversación

Utilice el comando `/chat new` sin reiniciar la CLI. Esto guarda su sesión actual en la base de datos y comienza una nueva:

```golpecito
## Iniciar una nueva conversación
/chatear nuevo

## Inicie una nueva conversación con un mensaje inicial
/chat nuevo ¿Cómo configuro un proyecto de React?
```

Utilice `/chat resume` para volver a cualquier sesión anterior.

#### Guardar y cargar conversaciones manualmente

Mientras estás en una sesión de chat:

```golpecito
## Guardar la conversación actual en un archivo JSON
/guardar chat ./mi-conversación-de-proyecto
/chat save ./mi-proyecto-conversación -f # sobrescribir existente
/guardar chat /home/usuario/proyecto/mi-proyecto-conversación.json

## Cargar una conversación desde un archivo JSON previamente guardado
/carga de chat ./mi-proyecto-conversación.json
```

> Nota: No puede utilizar `~` para indicar su directorio de inicio en la ruta. Los comandos `/chat save` y `/chat load` operan independientemente del directorio donde se creó originalmente la conversación.

---

*📂 Capítulo: **Chat > Subagents***

## Subagentes

> **Fuente:** [kiro.dev/docs/cli/chat/subagents/](https://kiro.dev/docs/cli/chat/subagents/)

---

Los subagentes le permiten asignar tareas complejas a agentes especializados con seguimiento del progreso en vivo. Kiro puede generar subagentes para que trabajen de forma independiente en subtareas mientras tú monitoreas el progreso en tiempo real.

---

### Capacidades clave

- **Ejecución autónoma**: se ejecuta de forma independiente con su propio contexto
- **Seguimiento del progreso en vivo**: supervise las actualizaciones de estado en tiempo real mientras trabajan los subagentes
- **Acceso a herramientas principales**: lea archivos, ejecute comandos, escriba archivos y use herramientas MCP
- **Ejecución paralela**: ejecute varios subagentes simultáneamente para una ejecución eficiente de las tareas.
- **Agregación de resultados**: los resultados se devuelven automáticamente al agente principal cuando se completan

---

### Subagente predeterminado

Kiro incluye un subagente predeterminado que maneja tareas de propósito general. Cuando asigna una tarea a un subagente sin especificar un agente personalizado, se utiliza el subagente predeterminado.

---

### Subagentes personalizados

Puede generar subagentes utilizando sus propias configuraciones de agente:

```
> Use the backend agent to refactor the payment module
```

El subagente hereda el acceso a la herramienta y la configuración de la configuración de ese agente.

---

### Cómo funcionan los subagentes

1. **Asignación de tareas**: usted describe una tarea; Kiro determina si un subagente es apropiado
2. **Inicialización de subagente**: creado con su propio contexto y acceso a herramientas
3. **Ejecución autónoma**: realiza la tarea de forma independiente (puede hacer una pausa para la aprobación del permiso de la herramienta)
4. **Actualizaciones de progreso**: recibirás actualizaciones de progreso en vivo que muestran el trabajo actual.
5. **Devolución de resultados**: cuando se completa, los resultados se devuelven al agente principal.

---

### Disponibilidad de herramientas

| Disponible | No disponible |
|---|---|
| `read` — Leer archivos y directorios | `web_search` — Investigación web |
| `write` — Crear y editar archivos | `web_fetch` — Obtener URL |
| `shell` — Ejecutar comandos bash | `introspección` - información CLI |
| `código` — Inteligencia de código | `pensamiento` — Herramienta de razonamiento |
| Herramientas MCP | `todo_list` — Seguimiento de tareas |
| | `use_aws` — Comandos de AWS |
| | `grep` — Buscar contenido del archivo |
| | `glob` — Buscar archivos por patrón |

Si la configuración de su agente personalizado incluye herramientas no disponibles, simplemente se omiten: el agente aún funciona con las herramientas disponibles.

---

### Configuración del acceso de subagente

#### Restringir agentes disponibles

En la configuración de su agente, especifique qué agentes se pueden usar como subagentes usando "allowedAgents".

#### Confiar en agentes específicos

Utilice `trustedAgents` para permitir que subagentes específicos se ejecuten sin solicitudes de permiso.

#### Combinando ambas configuraciones

Puede combinar `allowedAgents` y `trustedAgents` para obtener un control detallado sobre qué agentes se ejecutan automáticamente y cuáles requieren aprobación.

---

*📂 Capítulo: **Chat > Planning Agent***

## Agente del plan

> **Fuente:** [kiro.dev/docs/cli/chat/planning-agent/](https://kiro.dev/docs/cli/chat/planning-agent/)

---

El **Plan Agent** transforma ideas en planos de implementación estructurados antes de escribir código. Opera en modo **solo lectura** para mantenerse enfocado en el planeamiento.

---

### Empezando

| Método | comando |
|---|---|
| **Atajo de teclado** | `Shift + Tab` — alternar entre modo plan y ejecución |
| **Comando de barra diagonal** | `/plan` |
| **Con aviso inmediato** | `/plan Crear una API REST para la autenticación de usuarios` |

Al activarse, verás el indicador `[plan]` en tu aviso y un mensaje de bienvenida.

---

### Planificar el flujo de trabajo

#### 1. Recopilación de requisitos

El planificador te hace preguntas estructuradas para refinar tu idea inicial:

```
[plan] > Quiero crear una aplicación de tareas pendientes
Entiendo que quieres crear una aplicación de tareas pendientes. Déjame ayudarte a planificar esto.

[1]: ¿A qué plataforma debería apuntar esta aplicación de tareas pendientes?
a. Aplicación web b. Aplicación móvil c. Aplicación de escritorio d. Herramienta CLI

[2]: ¿Cuál es el caso de uso principal?
a. Gestión de tareas personales b. Colaboración en equipo c. Gestión de proyectos

(Utilice el chat para responder cualquier subconjunto: por ejemplo, "1=a, 2=b")
```

#### 2. Investigación y análisis

El planificador explora tu código base e investiga tecnologías relevantes.

#### 3. Plan de implementación

Genera un plan detallado paso a paso con objetivos claros:

```
**Plan de implementación: comando Todo CLI**

Planteamiento del problema: Agregar administración de tareas pendientes a la CLI existente.

Tarea 1: crear esquemas y modelos de base de datos
- Definir la estructura Todo con campos obligatorios
- Demostración: puede crear y consultar todos en la base de datos

Tarea 2: implementar la estructura de comandos CLI
- Agregar subcomando todo con operaciones de agregar/listar/completar
- Demostración: CLI acepta comandos de tareas pendientes y muestra ayuda
```

Cada tarea incluye: objetivos claros, guía de implementación, descripción de demostración.

#### 4. Aprobación y transferencia del plan

Antes de pasar a ejecución, el planificador solicita tu aprobación:

```
[plan] > ¿Este plan se ve bien o le gustaría que ajustara algo?
> ¡Se ve genial! Implementémoslo.

¡Planificación completa! ¿Listo para salir del agente [plan]? [t/n]: sí
```

El proceso de traspaso:
1. Aprobás el plan de implementación
2. Prompt interactivo confirma el cambio al modo de ejecución
3. Transición automática al agente anterior
4. El plan completo se pasa al agente de ejecución

---

### Diseño de solo lectura

El Plan Agent opera en modo **solo lectura** para mantener el foco en el planeamiento. No modifica archivos durante la fase de planificación.

---

### Mejores prácticas

1. **Usalo para tareas complejas** — más valioso para implementaciones de múltiples pasos
2. **Respondé las preguntas con detalle** — mejora la calidad del plan
3. **Dejalo explorar** — permití que analice tu código base existente
4. **Revisá los planes** — asegurate de que el plan coincide con tus expectativas antes del traspaso
5. **Iterá** — refinará hasta que el plan sea claro

---

### Ejemplo de flujo de trabajo

```
> /plan Agregar autenticación de usuario a mi aplicación web

[plan] > Según tengo entendido: desea implementar la autenticación de usuario.

[1]: ¿Qué método de autenticación prefieres?
a. Correo electrónico/contraseña b. OAuth c. Enlaces mágicos d. Multifactor
> 1=un

[2]: ¿Cuál es tu pila tecnológica actual?
d. Otro: especifique
> 2=d, estoy usando Rust con el framework Axum

*Investigando patrones de autenticación de Axum...*
*Explorando su estructura base de código existente...*

**Plan de implementación: sistema de autenticación de usuarios**
[Plan detallado...]

¿Se ve bien este plan? > ¡Se ve perfecto!
¿Listo para salir del agente [plan]? [t/n]: sí

[predeterminado] > Implementar este plan: [Plan transferido al agente de ejecución]
```

---

*📂 Capítulo: **Chat > Help Agent***

## Agente de ayuda

> **Fuente:** [kiro.dev/docs/cli/chat/help-agent/](https://kiro.dev/docs/cli/chat/help-agent/)

---

El **Agente de ayuda** es un agente integrado que responde preguntas sobre las características de Kiro CLI usando la documentación oficial.

---

### Inicio rápido

```golpecito
## Cambiar al Agente de Ayuda
> /ayuda

## Hacer una pregunta directamente
> /ayuda ¿Cómo configuro los servidores MCP?

## Listado clásico de comandos (heredado)
> /ayuda --legado
```

Al activarse:
```
✔ Cambiado a agente: kiro_help
[ayuda] >
```

---

### Lo que puedes preguntar

El Agente de Ayuda tiene acceso a la documentación completa de Kiro CLI:

| Categoría | Ejemplos |
|---|---|
| **Comandos** | Comandos de barra diagonal (`/chat`, `/agent`, `/context`) y comandos CLI (`kiro-cli chat`, `kiro-cli settings`) |
| **Herramientas** | Herramientas integradas: `fs_read`, `code`, `grep`, `glob` |
| **Configuración** | Cualquier configuración disponible vía `kiro-cli settings` |
| **Características** | Modo tangente, Hooks, MCP, Inteligencia de código, Subagentes |
| **Atajos** | Atajos de teclado y cómo usarlos |

---

### Creando configuración

El Agente de Ayuda puede crear y modificar archivos en directorios `.kiro/`:

```
[help] > Create an agent for writing tests
✔ Created .kiro/agents/test-writer.yaml
I've created a test-writing agent. Switch with: /agent swap test-writer
```

Puede crear:
- Agentes en `.kiro/agents/`
- Indicaciones en `.kiro/prompts/`
- Configuraciones LSP en `.kiro/`

---

### Ejemplos

#### Preguntar sobre un comando
```
[ayuda] > ¿Cómo guardo una conversación?
Utilice `/chat save` para guardar su conversación actual:
  /guardar chat ~/mi-sesión.json
Las conversaciones guardadas se pueden cargar más tarde con /chat load.
```

#### Pregunte acerca de una herramienta
```
[ayuda] > ¿Qué hace la herramienta de código?
La herramienta de código proporciona inteligencia de código:
• search_symbols: busca definiciones de símbolos por nombre
• lookup_symbols: obtiene detalles de símbolos específicos
• get_document_symbols: enumera todos los símbolos en un archivo
• Pattern_search: búsqueda estructural basada en AST
```

#### Preguntar sobre la configuración
```
[ayuda] > ¿Cómo habilito el modo tangente?
Habilite el modo tangente con:
  configuración de kiro-cli chat.enableTangentMode verdadero
O use /tangent durante una sesión de chat para alternarlo.
```

---

### Volviendo a su agente anterior

Ejecutá `/help` de nuevo mientras estés en el Help Agent para volver al agente anterior:

```
[help] > /help
✔ Switched to agent: kiro_default
```

O usamos `/agent swap <nombre>` para cambiar a un agente específico.

---

### Relacionado

- [Comandos de barra diagonal →] (https://kiro.dev/docs/cli/reference/slash-commands)
- [Agentes personalizados →](https://kiro.dev/docs/cli/custom-agents)
- [Referencia de configuración →](https://kiro.dev/docs/cli/reference/settings)

---

*📂 Capítulo: **Chat > Prompts***

## Indicaciones

> **Fuente:** [kiro.dev/docs/cli/chat/manage-prompts/](https://kiro.dev/docs/cli/chat/manage-prompts/)

---

Los avisos permiten crear, organizar y reutilizar instrucciones personalizadas para interacciones eficientes con el CLI.

---

### Tipos de mensajes

| Tipo | Descripción |
|---|---|
| **Mensajes locales** | Avisos específicos del proyecto, almacenados en el espacio de trabajo |
| **Mensajes globales** | Avisos disponibles en todos los proyectos |
| **Mensajes de MCP** | Avisos provistos por servidores MCP con funcionalidad extendida |

---

### Comandos

Todo el manejo de avisos se accede vía `/prompts`:

#### Lista de mensajes
```
/lista de mensajes
```
Muestra todos los mensajes disponibles en diseño de 3 columnas: nombre, descripción y origen.

#### Crear mensajes
```
/prompts create --name <nombre> [--content <contenido>]
```
- Si `--content` está provisto: crea el aviso con ese contenido
- Si no hay contenido: abre el editor por defecto
- Se guarda en `.kiro/prompts/` del espacio de trabajo actual
- Nombre máximo: 50 caracteres

#### Editar mensajes
```
/solicita editar <nombre>
```
Abre el mensaje en el editor por defecto. Soporta solicita locales, globales y MCP.

#### Ver detalles del mensaje
```
/solicita detalles <nombre>
```
Muestra: metadatos, argumentos, contenido completo, parámetros requeridos y origen.

---

### Uso de indicaciones

Invocará avisos en el chat con el prefijo `@`:

```bash
@prompt-name
@code-review          # Usa tu prompt local code-review
@src/auth.rs          # Incluye el contenido del archivo src/auth.rs
@crates/agent/        # Muestra la estructura del directorio
```

#### Referencias de archivos y directorios (v1.26.0+)

También podés usar `@` para referenciar archivos y directorios:

```bash
> Review @src/auth.rs for security issues
> What's the structure of @crates/agent/?
> Check @"my file.txt" for errors
> Compare @./v1/api.rs with @./v2/api.rs
```

**Características:**
- Completar tabulación después de `@`
- Referencias resaltadas en violeta
- Archivos como bloques de código, directorios como árbol
- Límite: 250 KB por archivo, 3 niveles de profundidad, 10 elementos por nivel

**Reglas de prioridad:**
1. **Indica a conocidos** (local, global, MCP)
2. **Archivos** — ruta de archivo
3. **Directorios** — si no es archivo

---

### Ubicaciones de almacenamiento

| Alcance | Ubicación | Prioridad |
|---|---|---|
| **Local (espacio de trabajo)** | `proyecto/.kiro/prompts/` | ⬆️Más alta |
| **Global (todo el usuario)** | `~/.kiro/prompts/` | Medios |
| **MCP** | Información sobre el servidor MCP | ⬇️Más baja |

---

### Integración MCP

Los avisos de MCP son provistos por servidores MCP configurados. Soportan argumentos dinámicos:

```bash
> /prompts list        # Los prompts MCP aparecen con su origen
> /prompts details aws-docs  # Ver parámetros requeridos
```

---

*📂 Capítulo: **Chat > File references***

## Referencias de archivos

> **Fuente:** [kiro.dev/docs/cli/chat/file-references/](https://kiro.dev/docs/cli/chat/file-references/)

---

Incluya contenidos de archivos o listados de directorios en línea en sus mensajes usando la sintaxis `@path`.

---

### Uso básico

Escriba `@` seguido de una ruta de archivo o directorio:

```
@src/index.ts          # Include file contents
@src/                  # Include directory tree
@./relative/path       # Relative paths
@"path with spaces.txt" # Quoted paths (required for spaces)
```

Las referencias pueden aparecer en cualquier parte de su mensaje:

```
Review @src/auth.ts for security issues
Compare @old.json with @new.json
What's in @src/ that handles authentication?
```

---

### Completar pestaña

Presione `Tab` después de `@` para completar automáticamente las rutas:

```
@src/<Tab>           # Shows files in src/
@package<Tab>        # Completes to @package.json
@"Screenshot 2024<Tab>   # Completes to @"Screenshot 2024-01.png"
```

La finalización funciona en cualquier parte de la línea de entrada. Las comillas se agregan automáticamente para los caminos con espacios.

---

### Cómo se resuelven las referencias

Cuando una referencia puede coincidir tanto con un mensaje como con un archivo:
1. **Preguntas primero**: si `@nombre` coincide con una petición de `/lista de peticiones`, se trata como una petición
2. **Archivos segundo**: de lo contrario, se marca como ruta de archivo
3. **Directorios terceros**: si no es un archivo, se marca como directorio

Forzar resolución de archivos: `@./myfile`

---

### Manejo de archivos

- **Compatible:** Archivos de texto (código fuente, configuración, Markdown) de hasta **250 KB**
- **No compatible:** Archivos binarios (imágenes, ejecutables, archivos): muestra un error
- **Archivos grandes:** Truncado a 250 KB con una advertencia: `⚠ El archivo 'large-file.json' fue truncado`

---

### Árboles de directorios

`@src/` se expande a una lista de árbol:

```
src/
├── lib/
│   ├── auth.ts
│   └── utils.ts
├── index.ts
└── config.json
```

**Límites:**
- Profundidad máxima: 3 niveles
- Máximo de elementos por nivel: 10 (muestra "... (N más elementos)" si se excede)
- Ignora: `node_modules`, `.git`, `target`, `dist`, `build`

---

### Ejemplos

```
> Review @src/auth.ts for security issues
> What's different between @v1/handler.py and @v2/handler.py?
> What's the structure of @infra/cdk/?
> Using the config in @serverless.yml, update @src/lambda/index.ts
```

---

### Limitaciones actuales

- Archivos de texto de hasta 250 KB únicamente (los archivos más grandes se truncan)
- Árboles de directorios de hasta 3 niveles de profundidad, 10 elementos por nivel
- Solo rutas explícitas: no hay patrones globales como `@*.ts`
- Solo el contenido completo del archivo: no hay rangos de líneas como `@file.ts:10-20`
- Sin expansión de tilde como `@~/file`
- Los archivos binarios no son compatibles

---

*📂 Capítulo: **Chat > Context management***

## Gestión del contexto

> **Fuente:** [kiro.dev/docs/cli/chat/context/](https://kiro.dev/docs/cli/chat/context/)

---

### Elegir el enfoque contextual adecuado

| Escenario | Enfoque |
|---|---|
| Archivos de proyecto esenciales (README, configuraciones, estándares) | **Recursos para agentes** |
| Grandes bases de código o conjuntos de documentación | **Bases de conocimiento** |
| Archivos temporales para la tarea actual | **Contexto de la sesión** |

---

### Gestión del contexto

#### Contexto persistente a través de recursos del agente

La forma recomendada de configurar el contexto es a través del campo "recursos" en la configuración de su agente. Esto crea un contexto persistente disponible en cada sesión.

```json
{
  "name": "my-agent",
  "description": "My development agent",
  "resources": [
    "file://README.md",
    "file://docs/**/*.md",
    "file://src/config.py"
  ]
}
```

**Esquemas de URI de recursos:**
- `file://` — Archivos cargados directamente en contexto al inicio
- `skill://` — Skills con metadatos cargados al inicio, contenido completo bajo demanda
- `knowledgeBase` — Contenido indexado buscado bajo demanda (configurado como objetos)

#### Contexto de sesión temporal

Agregue archivos a la sesión actual solo con `/context add`:

```
> / contexto agregar README.md
Se agregaron 1 ruta(s) al contexto.

> /contexto agregar documentos/*.md
Se agregaron 3 rutas al contexto.
```

⚠️ El contexto de la sesión **no es persistente**: no está disponible en sesiones nuevas.

#### Bases de conocimientos (para grandes conjuntos de datos)

Para bases de código grandes o documentación que excedería los límites de la ventana de contexto:

```bash
kiro-cli settings chat.enableKnowledge true
```

```
> /knowledge add /path/to/large-codebase --include "/*.py" --exclude "node_modules/"
```

Las bases de conocimiento se buscan bajo demanda cuando es relevante, ideal para materiales de referencia de gran tamaño.

#### Compactación de conversaciones

La compactación resume los mensajes más antiguos para liberar espacio en la ventana contextual.

- **Manual:** `/compacto`
- **Automático:** Se activa cuando la ventana de contexto se desborda

Después de la compactación, se crea una nueva sesión. Reanudar el original a través de `/chat resume`.

#### Visualización del uso del contexto

```
> /context show
Current context window (5.9% used)
  Context files    0.9%
  Tools            0.5%
  Kiro responses   0.7%
  Your prompts     3.8%
```

---

### Eliminando contexto

Utilice `/context remove <ruta>` para eliminar archivos específicos del contexto de la sesión actual.

---

### Mejores prácticas

- **Organización de archivos de contexto**: archivos relacionados con el grupo; usar patrones globales para directorios
- **Rendimiento**: evite cargar archivos binarios o generados automáticamente de gran tamaño (node_modules, dist, build)
- **Seguridad**: nunca agregue archivos que contengan secretos o credenciales a los recursos del agente

---

*📂 Capítulo: **Chat > Responding to messages***

## Responder a mensajes

> **Fuente:** [kiro.dev/docs/cli/chat/responding/](https://kiro.dev/docs/cli/chat/responding/)

---

El comando `/reply` abre su editor precargado con la respuesta más reciente de Kiro, citada como referencia. Luego puede agregar sus respuestas en línea y enviarlas.

---

### Cómo funciona

1. **Recupera la última respuesta**: busca el mensaje del asistente más reciente
2. **Formatos con comillas**: cada línea tiene el prefijo `>` para una atribución clara.
3. **Abre el editor**: su editor predeterminado se abre con el contenido citado.
4. **Edite y responda**: agregue sus respuestas a continuación o intercalelas con el texto citado
5. **Enviar**: cuando guarda y cierra el editor, se envía su respuesta.

---

### Comportamiento del editor

- **Contenido precargado**: el editor abre con la respuesta de Kiro ya citada.
- **Formato de cotización**: cada línea tiene el prefijo `>` para distinguirla visualmente.
- **Edición flexible**: agregue contenido en cualquier lugar: debajo de comillas, entre líneas o intercalado
- **Envío automático**: el contenido se envía automáticamente cuando el editor se cierra correctamente.

---

### Casos de uso

#### Respondiendo a múltiples preguntas

Cuando Kiro hace varias preguntas aclaratorias:

```
> What programming language are you using?
Python
> What framework are you working with?
Django
> What specific error are you encountering?
I'm getting a 404 error when trying to access my API endpoints.
```

#### Abordar puntos específicos

Responda a partes específicas de una explicación detallada:

```
> Here are three approaches you could take:
> 1. Use a database migration
> 2. Update the model directly
> 3. Create a custom management command
I'd like to go with option 1. Can you show me how to create the migration?
> Make sure to backup your data first.
Already done - I have a full backup from this morning.
```

#### Proporcionar comentarios estructurados

Organice las respuestas a múltiples sugerencias:

```
> I recommend these improvements:
> - Add error handling for network requests
> - Implement input validation
> - Add logging for debugging
Agreed on all points.
For the error handling: - Should I use try/catch blocks or a decorator pattern?
For logging: - What level of detail do you recommend?
```

---

### Mensajes de estado

| Estado | Mensaje |
|---|---|
| Éxito | "Contenido cargado desde el editor. Mensaje de envío..." |
| Sin cambios | "No se realizaron cambios en el editor, no se enviaron". |
| Ningún mensaje | "No se encontró ningún mensaje del asistente al que responder". |
| Error del editor | "Error al abrir el editor: [detalles del error específico]" |

---

*📂 Capítulo: **Chat > Permissions***

## Gestión de permisos de herramientas

> **Fuente:** [kiro.dev/docs/cli/chat/permissions/](https://kiro.dev/docs/cli/chat/permissions/)

---

Kiro CLI utiliza un sistema de permisos granular que le permite controlar exactamente qué herramientas pueden ejecutarse automáticamente y cuáles requieren su aprobación cada vez.

---

### Comandos de herramientas

| Comando | Acción |
|---|---|
| `/herramientas` | Ver el estado de los permisos para todas las herramientas actuales |
| `/tools confianza <herramienta>` | Confíe en una herramienta específica para la sesión actual |
| `/tools no es de confianza <herramienta>` | Desconfiar de una herramienta específica para la sesión actual |
| `/tools confianza-todo` | Confíe en todas las herramientas a la vez (úselas con precaución) |
| `/restablecer herramientas` | Restablecer permisos a los valores predeterminados |

```bash
$ kiro-cli chat
Kiro> /tools
Kiro> /tools trust read
Kiro> /tools untrust shell
Kiro> /tools trust-all
```

**Estados de permiso:**
- **Confiable**: Kiro puede usar la herramienta sin pedir commit
- **Por solicitud** — Kiro debe solicitar tu commit cada vez

> ⚠️ `/tools trust-all` conlleva riesgos de seguridad. Consulte [Usar /tools trust-all de forma segura](https://kiro.dev/docs/cli/chat/security/#using-tools-trust-all-safely).

---

### Herramientas disponibles

| Herramienta | Descripción |
|---|---|
| `leer` | Leer archivos y directorios |
| `escribir` | Crear y editar archivos |
| `cáscara` | Ejecutar comandos bash |
| `aws` | Integración de la CLI de AWS |
| `informe` | Información del informe |

---

### Niveles de confianza del comando Shell

Cuando Kiro solicita ejecutar un comando de shell, obtienes un **selector de confianza escalonado** en lugar de todo o nada:

```
Press (↑↓) to navigate (⏎) to select scope
> Full command    → git pull --rebase
  Partial command → git pull *
  Base command    → git *
  Entire Tool     → *
```

**Niveles de confianza (más → menos restrictivos):**

| Nivel | Ejemplo | Cubiertas |
|---|---|---|
| Comando completo | `git pull --rebase` | Sólo este comando exacto |
| Comando parcial | `git pull *` | Cualquier variante de `git pull` |
| Comando base | `git *` | Todos los comandos de git |
| Herramienta completa | `*` | Todos los comandos del shell |

Después de seleccionar, Kiro confirma: ` ✓ Confiable: git pull --rebase`

Los patrones confiables persisten durante la sesión y se almacenan como expresiones regulares en "allowedCommands".

> Si un comando coincide con un patrón `deniedCommands`, las opciones granulares no están disponibles; solo permita una vez o confíe en toda la herramienta.

---

### Niveles de confianza de ruta de lectura y escritura

Cuando Kiro accede a archivos **fuera del directorio de trabajo actual**, obtienes un selector de ruta específica:

```
Press (↑↓) to navigate (⏎) to select scope
> Specific paths    → ~/.config/app/settings.json
  Complete directory → ~/.config/app
  Entire Tool        → *
```

> Las rutas **dentro** del directorio de trabajo actual NO activan el selector.

---

*📂 Capítulo: **Chat > Working with Git***

## Trabajando con Git

> **Fuente:** [kiro.dev/docs/cli/](https://kiro.dev/docs/cli/)

---

Kiro CLI puede trabajar junto a Git para tareas como revisar cambios, generar commits, analizar diferencias y gestionar ramas.

---

### Flujos de trabajo comunes de Git

#### Revisar los cambios antes de comprometerlos

```bash
> Review the staged changes and suggest a commit message
> What files have been modified? Give me a summary of the changes
> Does this diff introduce any security issues?
```

#### Generando mensajes de commit

Podés pedirle a Kiro que analice los cambios actuales y genere un mensaje de commit convencional:

```bash
> Generate a conventional commit message for the staged changes
```

#### Analizando diferencias

```bash
> @src/auth.rs What changed in this file compared to main?
> Explain the changes in the last commit
```

---

### Uso de herramientas de comparación personalizadas

Podés configurar una herramienta de diferenciación externa para visualizar los cambios propuestos por Kiro:

```bash
kiro-cli settings chat.diffTool delta
kiro-cli settings chat.diffTool "delta --side-by-side"
```

Ver [Herramientas de diferenciación personalizadas →](./14_Custom%20diff%20tools.md) para más detalles.

---

### Consejos para flujos de trabajo de Git

- Usá `@` para referenciar archivos específicos: `> Revise @src/main.rs para detectar problemas antes de confirmar`
- Combiná con Hooks para automatizar acciones en eventos Git (pre-commit, post-merge)
- Usá el Plan Agent (`/plan`) para planificar características antes de cometer cambios
- El agente puede leer la salida de `git status`, `git diff`, `git log` directamente desde el terminal integrado

---

### Relacionado

- [Herramientas de diferenciación personalizadas →](./14_Custom%20diff%20tools.md)
- [Hooks →](https://kiro.dev/docs/cli/hooks/)
- [Referencias de archivos →](./05_Prompts.md#file-and-directory-references-v1260)

---

*📂 Capítulo: **Chat > Images***

## Trabajar con imágenes

> **Fuente:** [kiro.dev/docs/cli/chat/images/](https://kiro.dev/docs/cli/chat/images/)

---

Kiro puede analizar y discutir imágenes directamente en su sesión de chat.

---

### Métodos para compartir imágenes

#### 1. Arrastrar y soltar

Arrastre una imagen directamente a la ventana de su terminal:
1. La ruta de la imagen se inserta automáticamente en su mensaje.
2. Agregue texto para proporcionar contexto.
3. Kiro procesa y responde según el contenido de la imagen.

```
Kiro> /path/to/architecture-diagram.png Can you explain this architecture and generate sample code?
```

#### 2. Usando la herramienta `leer`

Archivos de imagen de referencia explícita:

```
Kiro> Can you analyze this screenshot at /path/to/screenshot.png?
```

Kiro sugiere automáticamente usar `fs_read` con el modo Imagen cuando mencionas archivos de imagen.

#### 3. Pegar desde el portapapeles

Pegue una imagen del portapapeles de su sistema:

```
/paste
```

---

### Casos de uso de imágenes

- Análisis de capturas de pantalla de mensajes de error para solucionar problemas.
- Convertir diagramas de arquitectura en implementaciones de código.
- Discutir diseños UI/UX y generar HTML/CSS correspondiente.
- Comprender diagramas de flujo y traducirlos en algoritmos.
- Revisar fragmentos de código compartidos como imágenes.
- Interpretación de esquemas técnicos para documentación.

---

### Formatos admitidos y limitaciones

| Propiedad | Valor |
|---|---|
| **Formatos** | JPEG/JPG, PNG, GIF, WebP |
| **Tamaño máximo** | 10 MB por imagen |
| **Máximo de imágenes por solicitud** | 10 |

**Mejores prácticas:**
- Utilice imágenes de alta resolución con texto claro
- Proporciona instrucciones específicas sobre lo que quieres que haga Kiro.
- Para diagramas complejos, proporcione contexto adicional

---

*📂 Capítulo: **Chat > Security considerations***

## Consideraciones de seguridad

> **Fuente:** [kiro.dev/docs/cli/chat/security/](https://kiro.dev/docs/cli/chat/security/)

---

### Comprender los riesgos de seguridad

Al usar Kiro, tuvo en cuenta los siguientes riesgos potenciales:

| Riesgo | Ejemplo |
|---|---|
| **Cambios no deseados al sistema** | Kiro puede interpretar solicitudes de forma inesperada |
| **Modificaciones a recursos AWS** | Recursos pueden crearse, modificarse o eliminarse, afectando entornos productivos o generando costos |
| **Pérdida de datos** | Comandos que eliminan o sobreescriben archivos |
| **Vulnerabilidades de seguridad** | Comandos que comprometen la seguridad del sistema |

Estos riesgos se incrementan significativamente al usar `/tools trust-all` o `/acceptall`, que pasan por alto las commits.

**Ejemplos concretos:**
- `"limpiar archivos antiguos"` → puede eliminar archivos de configuración importantes
- `"optimizar mis instancias EC2"` → puede terminar instancias en ejecución
- `"solucionar problemas de seguridad"` → puede modificar permisos exponiendo datos sensibles

> ⚠️ **No uses `/tools trust-all` o `/acceptall` en entornos productivos o con datos sensibles. Sos responsable de todas las acciones ejecutadas por Kiro.**

---

### Mejores prácticas generales de seguridad

#### Restringir el acceso a archivos

Por defecto, Kiro puede leer archivos sin pedir permiso. Para entornos sensibles, podría restringir esto:

```bash
/tools untrust read
```

Con esta configuración, Kiro pedirá permiso explícito antes de leer cualquier archivo.

Para hacerlo persistente, agregue a su script de inicio de shell:
```golpecito
echo 'alias kiro-cli="kiro-cli --untrust-fs-read"' >> ~/.bashrc
```

#### Medidas de seguridad adicionales

Para entornos con información altamente sensible:

- Usá Kiro en un entorno de desarrollo dedicado que **no contiene** credenciales sensibles o datos privados
- Almacená archivos sensibles fuera de tus directorios de proyecto o en ubicaciones con permisos restringidos
- Usamos variables de entorno para valores sensibles en lugar de codificarlos en archivos
- Considerá usar `/tools untrust aws` para requerir permiso explícito antes de hacer llamadas a la API de AWS
- Usá Steering para definir pautas y restricciones de seguridad

#### Usando `/tools trust-all` de forma segura

Si tienes que usar `/tools trust-all` o `/acceptall` para flujos de trabajo específicos:

| Práctica | Descripción |
|---|---|
| Solo en desarrollo/pruebas | **Nunca** en producción |
| Alcance temporal | Habilitá solo para tareas específicas → deshabilitat con `/tools reset` |
| Copia de seguridad anterior | Realice una copia de seguridad de datos importantes antes de habilitarlo |
| Permisos mínimos | Usa credenciales AWS con permisos mínimos |
| Monitoreo activo | Monitoreá todas las acciones de Kiro mientras está habilitado |

Para volver a los permisos por defecto:
```golpecito
/restablecer herramientas
```

Esto revierte todas las herramientas a sus niveles de permiso por defecto (solo Readtrusted).

---

### Relacionado

- [Permisos →](./09_Permissions.md)
- [Configuración →](./13_Configuration.md)
- [Protección de datos →](../../01_IDE/15_Privacy%20and%20security/01_Data%20protection.md)

---

*📂 Capítulo: **Chat > Configuration***

## Configuración

> **Fuente:** [kiro.dev/docs/cli/chat/configuration/](https://kiro.dev/docs/cli/chat/configuration/)

---

Kiro CLI puede configurarse en tres ámbitos para adaptarse a tus preferencias y estándares de equipo.

---

### Rutas del archivo de configuración

| Alcance | Ubicación | Descripción |
|---|---|---|
| **Global** | `~/.kiro/` | Aplica a todos los proyectos donde se usa Kiro |
| **Proyecto** | `<raíz-proyecto>/.kiro` | Específico al proyecto |
| **Agente** | `<inicio-usuario\|raíz-proyecto>/.kiro/agents` | Definido en el archivo de configuración del agente |

#### Referencia de archivos de configuración

| Archivo | Alcance |
|---|---|
| `~/.kiro/settings/mcp.json` | PCM global |
| `.kiro/settings/mcp.json` | Proyecto MCP |
| `~/.kiro/prompts` | Avisos globales |
| `.kiro/prompts` | Indicaciones del proyecto |
| `~/.kiro/agentes` | Agentes Globales |
| `.kiro/agentes` | Agentes de Proyectos |
| `~/.kiro/steering` | Steering Global |
| `.kiro/steering` | Steering de Proyectos |
| `~/.kiro/settings/cli.json` | Configuración CLI global |

---

### Resolución de conflictos de configuración

Los conflictos de configuración se resuelven eligiendo la configuración **más cercana al contexto actual**:

> Si tienes una configuración MCP en los archivos `mcp.json` global y del proyecto, cuando chateas en la carpeta del proyecto, se aplica la configuración MCP del proyecto.

**Orden de prioridad:**

```
Agent config  >  Project config  >  Global config
```

> Para servidores MCP, la prioridad es diferente. Ver [prioridad de carga del servidor MCP →] (https://kiro.dev/docs/cli/mcp/#mcp-server-loading-priority)

---

### Configuraciones comunes

Podés gestionar la configuración vía CLI:

```golpecito
## Ver una configuración
configuración de kiro-cli chat.diffTool

## Establecer un ajuste
configuración de kiro-cli chat.diffTool delta
configuración de kiro-cli chat.enableTangentMode verdadero

## Eliminar una configuración (vuelve al valor predeterminado)
configuración de kiro-cli -d chat.diffTool
```

---

*📂 Capítulo: **Chat > Custom diff tools***

## Herramientas de diferenciación personalizadas

> **Fuente:** [kiro.dev/docs/cli/chat/diff-tools/](https://kiro.dev/docs/cli/chat/diff-tools/)

---

Podrá configurar herramientas de diferencias externas para visualizar los cambios de código propuestos por Kiro CLI.

---

### Configuración

Configura tu herramienta de diferenciación preferida con la configuración `chat.diffTool`:

```golpecito
## Configurar una herramienta
configuración de kiro-cli chat.diffTool delta

## Con argumentos personalizados
configuración de kiro-cli chat.diffTool "delta --side-by-side"

## Restablecer el diferencial integrado
configuración de kiro-cli -d chat.diffTool
```

---

### Herramientas terminales

Muestran diferencias directamente en la terminal — mantienen el flujo de trabajo:

| Herramienta | comando |
|---|---|
| [delta](https://github.com/dandavison/delta) | `delta` |
| [difftastic](https://github.com/Wilfred/difftastic) | `diferente` |
| [icdiff](https://github.com/jeffkaufman/icdiff) | `icdiff` |
| [diff-so-fancy](https://github.com/so-fancy/diff-so-fancy) | `diferente-tan-elegante` |
| [colordiff](https://www.colordiff.org/) | `colordiff` |
| [ydiff](https://github.com/ymattw/ydiff) | `ydiff` |
| [murciélago](https://github.com/sharkdp/bat) | `murciélago` |

---

### Herramientas GUI

Abra una ventana separada para revisar cambios:

| Herramienta | comando |
|---|---|
| Código VS | `código` |
| VSCodio | `codio` |
| Merge | `merge` |
| KDiff3 | `kdiff3` |
| Combinación de archivos (macOS) | `opendiff` |
| Vim | `vimdiff`/`vim`/`nvim` |

> ⚠️ Las herramientas GUI abren archivos temporales solo para visualización. Las ediciones que hagas en la GUI **no se guardan ni aplican** a los cambios propuestos por Kiro.

---

### Argumentos personalizados

Podés personalizar el comportamiento incluyendo argumentos entre comillas:

```bash
## Side-by-side view con delta
kiro-cli settings chat.diffTool "delta --side-by-side"
```

---

### Otras herramientas

Kiro puede trabajar con herramientas no listadas. Cuando configuras una herramienta, Kiro intenta dos enfoques:
1. Envía un unified diff a la herramienta vía stdin
2. Invoca la herramienta con dos rutas de archivos temporales como argumentos

Si ningún enfoque funciona, Kiro vuelve al diff inline integrado.

---

### Solución de problemas

Si ves el error `"No se pudo encontrar la herramienta de diferenciación"`, la herramienta no está instalada o no está en tu RUTA:

```golpecito
## Verificar que está en el PATH
cual delta

## Delta instalador
##macOS
instalar cerveza git-delta

##Ubuntu/Debian
sudo apto instalar git-delta
```

Consulte la documentación de la herramienta específica para instrucciones de instalación.

---

*📂 Capítulo: **Custom agents > Creating custom agents***

## Creando agentes personalizados

> **Fuente:** [kiro.dev/docs/cli/custom-agents/creating/](https://kiro.dev/docs/cli/custom-agents/creating/)

---

Los agentes personalizados te permiten crear asistentes de IA especializados para flujos de trabajo específicos.

---

### Inicio rápido

Desde una sesión de chat de Kiro CLI:

```
> /agent create
✔ Enter agent name: · backend-specialist
✔ Enter agent description: · You are a specialist in backend coding practices
✔ Agent scope · Local (current workspace)
Select MCP servers: markdown-downloader (node), code-analysis (uv)
✓ Agent 'backend-specialist' has been created and saved successfully!
```

También podés proporcionar nombre y opciones en línea:

```
> /agent create backend-specialist -D "Backend coding specialist" -m code-analysis
```

O desde la terminal directamente:

```bash
kiro-cli agent create backend-specialist
```

> `/agent generate` es un alias de `/agent create`. Ambos comandos se comportan de manera idéntica.

---

### Opciones

| Bandera | Descripción | Disponible en |
|---|---|---|
| `--directorio` | Dónde guardar el agente | Ambos |
| `--de` | Basar en un agente existente | Ambos |
| `--manual` | Manual de modo de creación (editor) | Ambos |
| `--descripción` / `-D` | Descripción del agente | Solo asistido por IA |
| `--mcp-server` / `-m` | Servidor MCP a incluir | Solo asistido por IA |

> `--description` y `--mcp-server` no pueden usarse con `--manual` ni `--from`.

#### Valores del directorio

| Valor | Ubicación |
|---|---|
| `espacio de trabajo` | `.kiro/agents/` (proyecto actual) |
| `global` | `~/.kiro/agents/` (todos los proyectos) |
| `./ruta` o `/ruta` | Ruta personalizada |

Sin `--directory`, los agentes se guardan en el directorio global (`~/.kiro/agents/`).

#### Modo de creación manual

Para definir la configuración usted mismo en un editor:

```
> /agent create my-agent --manual
```

Para basar un nuevo agente en uno existente:

```
> /agent create my-agent --from backend-specialist
```

---

### Archivo de configuración del agente

Los agentes personalizados se definen con archivos de configuración JSON:

```json
{
  "name": "my-agent",
  "description": "A custom agent for my workflow",
  "tools": ["read", "write"],
  "allowedTools": ["read"],
  "resources": [
    "file://README.md",
    "file://.kiro/steering/**/*.md",
    "skill://.kiro/skills/**/SKILL.md"
  ],
  "prompt": "You are a helpful coding assistant",
  "model": "claude-sonnet-4"
}
```

---

### Usando su agente personalizado

```
> /agent swap
❯ rust-developer-agent
  kiro_default
  backend-specialist
```

Después de seleccionar:
```
✔ Elija uno de los siguientes agentes · especialista en backend
[especialista en backend] >
```

O iniciará directamente con tu agente:
```golpecito
kiro-cli --agente mi-agente
```

---

*📂 Capítulo: **Custom agents > Overview***

## Agentes personalizados - Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/custom-agents/](https://kiro.dev/docs/cli/custom-agents/)

---

Los agentes personalizados le permiten crear e implementar agentes de IA especializados adaptados a flujos de trabajo específicos, con un control detallado sobre las herramientas, el contexto y el comportamiento.

---

### Beneficios de utilizar agentes personalizados

1. **Optimización del flujo de trabajo**: cree agentes adaptados a tareas específicas como administración de infraestructura de AWS, revisiones de código o sesiones de depuración.
2. **Reducción de interrupciones**: apruebe previamente herramientas confiables para eliminar las solicitudes de permiso durante las sesiones de trabajo enfocadas.
3. **Contexto mejorado**: incluya automáticamente documentación relevante del proyecto, archivos de configuración o información del sistema.
4. **Colaboración en equipo**: comparta configuraciones de agentes personalizadas con los miembros del equipo para garantizar entornos de desarrollo consistentes.
5. **Control de seguridad**: limite el acceso a las herramientas solo a lo necesario para flujos de trabajo específicos, lo que reduce los posibles riesgos de seguridad.

---

### Relación con MCP y herramientas integradas

Los agentes personalizados trabajan tanto con herramientas integradas como con herramientas externas proporcionadas a través del Protocolo de contexto modelo (MCP):

- **Utilice herramientas integradas**: operaciones de archivos, ejecución de comandos, integración de AWS CLI y otras funciones principales
- **Integrar servidores MCP**: agregue herramientas y servicios personalizados a través de configuraciones de servidor MCP
- **Control de acceso a herramientas**: especifique exactamente qué herramientas de cada fuente están disponibles
- **Administrar conflictos de herramientas**: use alias para manejar conflictos de nombres entre diferentes fuentes de herramientas

---

### Próximos pasos

- [Creando agentes personalizados →](https://kiro.dev/docs/cli/custom-agents/creating/)
- [Referencia de configuración del agente →](https://kiro.dev/docs/cli/custom-agents/configuration-reference/)
- [Agentes compartidos →](https://kiro.dev/docs/cli/custom-agents/sharing/)

---

*📂 Capítulo: **Custom agents > Configuration reference***

## Referencia de configuración

> **Fuente:** [kiro.dev/docs/cli/custom-agents/configuration-reference/](https://kiro.dev/docs/cli/custom-agents/configuration-reference/)

---

### Campos de configuración

#### `nombre`
Nombre del agente para identificación y visualización.
```json
{ "nombre": "aws-experto" }
```

#### `descripción`
Descripción legible del propósito del agente.
```json
{ "description": "Un agente especializado en tareas de infraestructura de AWS" }
```

#### `aviso`
Contexto de alto nivel para el agente (similar a un aviso del sistema). Soporta texto en línea en `file://` URI.
```json
{ "prompt": "Usted es un experto especialista en infraestructura de AWS" }
{ "prompt": "archivo://./prompts/aws-expert.md" }
```
Rutas relativas se resuelven relativas al archivo de configuración del agente.

#### `mcpServidores`
Servidores MCP a los que el agente tiene acceso.
```json
{
  "mcpServers": {
    "fetch": { "comando": "fetch-server", "args": [] },
    "git": { "comando": "git-mcp", "args": [], "timeout": 120000 }
  }
}
```

| Campo | Requerido | Descripción |
|---|---|---|
| `comando` | ✅ | Comando para iniciar el servidor |
| `argumentos` | No | Argumentos para el comando |
| `entorno` | No | Variables de entorno |
| `tiempo de espera` | No | Tiempo de espera en ms (predeterminado: 120000) |

#### `herramientas`
Herramientas disponibles para el agente.
```json
{
  "herramientas": ["leer", "escribir", "shell", "@git", "@rust-analyzer/check_code"]
}
```

| Sintaxis | Descripción |
|---|---|
| `"leer"`, `"shell"` | Herramientas incorporadas |
| `"@nombre_servidor"` | Todas las herramientas de un servidor MCP |
| `"@nombre_servidor/nombre_herramienta"` | Herramienta específica de un servidor MCP |
| `"*"` | Todas las herramientas |
| `"@integrado"` | Todas las herramientas integradas |

#### `aliases de herramienta`
Remapea nombres de herramientas para resolver conflictos o crear nombres más intuitivos.
```json
{
  "alias de herramienta": {
    "@github-mcp/get_issues": "github_issues",
    "@gitlab-mcp/get_issues": "gitlab_issues"
  }
}
```

#### `herramientas permitidas`
Herramientas que pueden usarse sin pedir permiso (preaprobadas).
```json
{
  "allowedTools": ["leer", "@git/git_status", "@server/read_*", "@fetch"]
}
```
Soporta comodines: `"code_*"`, `"*_bash"`, `"@server/read_*"`.

#### `herramientasConfiguración`
Configuración específica para ciertas herramientas.
```json
{
  "Configuración de herramientas": {
    "escribir": { "allowedPaths": ["src/**", "pruebas/**", "Cargo.toml"] },
    "cáscara": {
      "allowedCommands": ["git status", "git fetch"],
      "deniedCommands": ["git commit.*", "git push.*"],
      "autoAllowReadonly": verdadero
    }
  }
}
```

#### `recursos`
Recursos locales disponibles para el agente.
```json
{
  "recursos": [
    "archivo://README.md",
    "archivo://.kiro/steering/**/*.md",
    "skill://.kiro/skills/**/SKILL.md"
  ]
}
```
- `file://` — Se carga en contexto al inicio
- `skill://` — Solo metadatos al inicio, contenido completo bajo demanda

**Base de conocimientos:**
```json
{
  "recursos": [{
    "tipo": "base de conocimientos",
    "fuente": "archivo://./docs",
    "nombre": "Documentos del proyecto",
    "indexType": "mejor",
    "actualización automática": verdadero
  }]
}
```

#### `hooks`
Comandos que corren en puntos específicos del ciclo de vida del agente.
```json
{
  "hooks": {
    "agentSpawn": [{ "comando": "estado de git" }],
    "userPromptSubmit": [{ "command": "ls -la" }],
    "preToolUse": [{ "matcher": "execute_bash", "command": "echo 'Running bash'" }],
    "postToolUse": [{ "matcher": "fs_write", "command": "cargo fmt --all" }],
    "detener": [{ "comando": "prueba npm" }]
  }
}
```

#### `modelo`
Modelo a usar para este agente. Si no se especifica, usa el modelo por defecto.
```json
{ "modelo": "claude-sonnet-4" }
```

#### `atajo de teclado`
Atajo de teclado para cambiar rápidamente a este agente.
```json
{ "tecladoAtajo": "ctrl+a" }
```
Formato: `[modificador+]clave`. Modificadores: `ctrl`, `shift`. Teclas: `a-z`, `0-9`.

#### `mensaje de bienvenida`
Mensaje que se muestra al activar el agente.

---

### Ubicaciones de archivos

| Alcance | Ubicación | Prioridad |
|---|---|---|
| **Local (espacio de trabajo)** | `.kiro/agents/<nombre>.json` | ⬆️Más alta |
| **Global (todo el usuario)** | `~/.kiro/agents/<nombre>.json` | Más baja |

---

### Ejemplo completo

```json
{
  "name": "aws-rust-agent",
  "description": "Specialized agent for AWS and Rust development",
  "prompt": "file://./prompts/aws-rust-expert.md",
  "mcpServers": {
    "fetch": { "command": "fetch-server", "args": [] },
    "git": { "command": "git-mcp", "args": [] }
  },
  "tools": ["read", "write", "shell", "aws", "@git", "@fetch/fetch_url"],
  "toolAliases": {
    "@git/git_status": "status",
    "@fetch/fetch_url": "get"
  },
  "allowedTools": ["read", "@git/git_status"],
  "toolsSettings": {
    "write": { "allowedPaths": ["src/**", "tests/**", "Cargo.toml"] },
    "aws": { "allowedServices": ["s3", "lambda"], "autoAllowReadonly": true }
  },
  "resources": ["file://README.md", "file://docs/**/*.md"],
  "hooks": {
    "agentSpawn": [{ "command": "git status" }],
    "postToolUse": [{ "matcher": "fs_write", "command": "cargo fmt --all" }]
  },
  "model": "claude-sonnet-4",
  "keyboardShortcut": "ctrl+shift+r",
  "welcomeMessage": "Ready to help with AWS and Rust development!"
}
```

---

### Mejores prácticas

1. **Empezá restrictivo** — Comenzá con acceso mínimo a herramientas y expandí según sea necesario
2. **Nombres claros** — Usá nombres descriptivos que indican el propósito del agente
3. **Documentá el uso** — Agrega descripciones claras para que los miembros del equipo entiendan el agente
4. **Control de versiones** — Almacená configuraciones de agentes en el repositorio del proyecto
5. **Tesear a fondo** — Verifica que los permisos de herramientas funcionen como se espera antes de compartir

---

*📂 Capítulo: **Custom agents > Examples***

## Ejemplos de agentes

> **Fuente:** [kiro.dev/docs/cli/custom-agents/examples/](https://kiro.dev/docs/cli/custom-agents/examples/)

---

### Agente especialista de AWS

```json
{
  "name": "aws-specialist",
  "description": "Specialized agent for AWS infrastructure management",
  "prompt": "You are an expert AWS infrastructure specialist. Help with CloudFormation, Lambda, S3, EC2, and other AWS services.",
  "tools": ["read", "write", "shell", "aws"],
  "allowedTools": ["read", "aws"],
  "toolsSettings": {
    "aws": {
      "allowedServices": ["s3", "lambda", "cloudformation"],
      "autoAllowReadonly": true
    }
  },
  "resources": ["file://README.md", "file://infrastructure/**/*.yaml"]
}
```

---

### Agente de flujo de trabajo de desarrollo

```json
{
  "name": "dev-workflow",
  "description": "Streamlined development workflow with pre-approved common operations",
  "prompt": "You are a development workflow assistant. Help with coding, testing, and deployment tasks.",
  "tools": ["read", "write", "shell", "@git"],
  "allowedTools": ["read", "@git/git_status", "@git/git_diff", "@git/git_log"],
  "toolsSettings": {
    "shell": {
      "allowedCommands": ["npm test", "npm run build", "git status", "git diff"],
      "autoAllowReadonly": true
    }
  },
  "hooks": {
    "postToolUse": [{ "matcher": "fs_write", "command": "npm run lint --fix" }]
  }
}
```

---

### Agente de revisión de código

```json
{
  "name": "code-reviewer",
  "description": "Focused code review agent with read-only access",
  "prompt": "You are an expert code reviewer. Analyze code for quality, security, performance, and maintainability.",
  "tools": ["read", "@git/git_diff"],
  "allowedTools": ["read", "@git/git_diff"],
  "resources": [
    "file://.kiro/steering/code-standards.md"
  ]
}
```

---

### Agente específico del proyecto

Para un agente específico de proyecto, guárdelo en `.kiro/agents/`:

```json
{
  "name": "my-project-agent",
  "description": "Agent configured for this specific project",
  "prompt": "file://./agent-prompts/project-context.md",
  "tools": ["read", "write", "shell"],
  "allowedTools": ["read"],
  "resources": [
    "file://README.md",
    "file://CONTRIBUTING.md",
    "file://docs/**/*.md",
    "skill://.kiro/skills/**/SKILL.md"
  ],
  "hooks": {
    "agentSpawn": [{ "command": "git status" }]
  }
}
```

---

### Integración remota del servidor MCP

```json
{
  "name": "api-agent",
  "description": "Agent with access to remote API via MCP",
  "mcpServers": {
    "my-api": {
      "type": "http",
      "url": "https://api.example.com/mcp"
    }
  },
  "tools": ["read", "@my-api"],
  "allowedTools": ["read", "@my-api/get_data"]
}
```

#### Con configuración OAuth

```json
{
  "name": "oauth-agent",
  "mcpServers": {
    "secure-api": {
      "type": "http",
      "url": "https://secure-api.example.com/mcp",
      "oauth": {
        "redirectUri": "127.0.0.1:8080",
        "oauthScopes": ["read", "write"]
      }
    }
  }
}
```

---

### Consejos para crear agentes personalizados eficaces

1. **Defina el alcance claramente** — Utilice `tools` y `allowedTools` para limitar exactamente qué puede hacer el agente
2. **Aprovechá los recursos** — Incluí documentación relevante del proyecto en `resources`
3. **Usá hooks para automatización** — `postToolUse` es ideal para formatear código automáticamente
4. **Comenzá simple** — Creá un agente básico y ampliará sus capacidades según sea necesario
5. **Compartí con el equipo** — Almacená agentes de equipo en `.kiro/agents/` y cometeá al repositorio

---

*📂 Capítulo: **Custom agents > Troubleshooting***

## Solución de problemas de agentes personalizados

> **Fuente:** [kiro.dev/docs/cli/custom-agents/troubleshooting/](https://kiro.dev/docs/cli/custom-agents/troubleshooting/)

---

### Errores de configuración

#### Sintaxis JSON no válida

**Síntomas:**
- Mensajes de error mencionando "JSON no válido" o "error de sintaxis"
- El agente no aparece en `/lista de agentes`
- Comportamiento de respaldo al agente por defecto

**Soluciones:**
- Validá el JSON con un linter online
- Revisar errores comunes de JSON:
  - Comas faltantes entre elementos
  - Comas al final del último elemento (comas al final)
  - Soportes o llaves sin cerrar
  - Comillas sin escapar en cuerdas
- Usaremos `/agent Scheme` para verificar la estructura de tu configuración.

#### Errores de validación del esquema

**Síntomas:**
- Advertencias sobre campos desconocidos
- Comportamiento que no coincide con la configuración
- Errores de campos requeridos faltantes

**Soluciones:**
- Comparará tu configuración contra el esquema con `/agent esquema`
- Buscá errores tipográficos en nombres de campos (ej. `allowedTools` vs `allowedTool`)
- Verifica que los tipos de datos coinciden (arrays vs strings, booleans vs strings)

---

### Problemas de carga del agente personalizado

#### Agente no encontrado

**Síntomas:**
- `/lista de agentes` no muestra tu agente
- Fallback al agente por defecto sin advertencia

**Soluciones:**
- Verifique la ubicación del archivo:
  - Global: `~/.kiro/agents/<nombre>.json`
  - Espacio de trabajo: `.kiro/agents/<nombre>.json`
- Verifica permisos de lectura del archivo
- Asegurate de que el nombre del archivo coincida con el nombre que intentas usar
- El archivo debe tener extensión `.json`

#### Cargando la versión incorrecta del agente

**Síntomas:**
- El comportamiento no coincide con los cambios recientes de configuración.
- Advertencia sobre conflictos de agentes

**Soluciones:**
- Los agentes locales tienen precedencia sobre los globales.
- Usaremos `/agent list` para ver qué versión está cargada
- Renombrá o eliminará archivos de agentes en conflicto

---

### Problemas con las herramientas

#### Herramienta no disponible

**Síntomas:**
- Errores sobre herramientas desconocidas o no disponibles
- El agente pide permiso para herramientas en `allowedTools`
- Herramientas de servidores MCP no funcionan

**Soluciones:**
- Verifique que los nombres de las herramientas estén correctamente escritos en el array `tools`
- Para herramientas MCP, asegúrese de que el servidor esté configurado en `mcpServers`
- Usá la sintaxis correcta: `@server_name/tool_name`

#### Solicitudes de permiso inesperadas

**Síntomas:**
- Solicita permiso para herramientas listadas en `allowedTools`

**Soluciones:**
- Asegurate de que las herramientas están en **ambos** arrays: `tools` Y `allowedTools`
- Revisá errores tipográficos entre los dos arrays.
- Para herramientas MCP, usará el nombre completo con prefijo del servidor en `allowedTools`
- Verifique que los `toolAliases` estén correctamente aplicados

---

### Comportamiento del agente de depuración

#### Lista de verificación de pruebas

```
1. Validar JSON: usar un JSON validator
2. Verificar schema: /agent schema
3. Listar agentes: /agent list
4. Cambiar al agente: /agent swap [nombre]
5. Testear cada tool individualmente
6. Verificar resources y hooks
7. Testear workflows completos
```

#### Problemas con el servidor MCP

- Verifica que los comandos del servidor MCP son correctos y los ejecutables están en tu PATH
- Verifique que las variables de entorno requeridas estén seleccionadas
- Testea los servidores MCP de forma independiente
- Revisará los logs del servidor MCP para mensajes de error
- Aumentá los valores de `timeout` si los servidores tardan en iniciar

---

*📂 Capítulo: **MCP > Configuration***

## Protocolo de contexto modelo (MCP): CLI

> **Fuente:** [kiro.dev/docs/cli/mcp/](https://kiro.dev/docs/cli/mcp/)

---

MCP es un protocolo que permite a Kiro comunicarse con servidores externos para acceder a información y herramientas especializadas.

Con MCP, puedes:
- Acceda a bases de conocimiento y documentación especializadas.
- Integrar con servicios externos y API.
- Amplíe las capacidades de Kiro con herramientas específicas de dominio
- Cree herramientas personalizadas para sus flujos de trabajo específicos

---

### Configuración de MCP

Hay dos formas de configurar servidores MCP en Kiro CLI:

#### 1. Línea de comando

```bash
kiro-cli mcp add \
  --name "awslabs.aws-documentation-mcp-server" \
  --scope global \
  --command "uvx" \
  --args "awslabs.aws-documentation-mcp-server@latest" \
  --env "FASTMCP_LOG_LEVEL=ERROR" \
  --env "AWS_DOCUMENTATION_PARTITION=aws"
```

#### 2. Archivo mcp.json

Los servidores MCP se pueden cargar desde:
- Nivel de espacio de trabajo: `<raíz del proyecto>/.kiro/settings/mcp.json`
- Nivel de usuario: `~/.kiro/settings/mcp.json`

```json
{
  "mcpServers": {
    "local-server-name": {
      "command": "command-to-run-server",
      "args": ["arg1", "arg2"],
      "env": {
        "ENV_VAR1": "value1",
        "ENV_VAR2": "value2"
      },
      "disabled": false
    },
    "http-server-with-oauth": {
      "type": "http",
      "url": "https://api.example.com/mcp",
      "oauth": {
        "redirectUri": "127.0.0.1:8080",
        "oauthScopes": ["read", "write"]
      }
    }
  }
}
```

Para servidores MCP basados en HTTP que requieren OAuth:
- `oauth.redirectUri` — URI de redireccionamiento personalizado para flujo OAuth (opcional)
- `oauth.oauthScopes`: conjunto de alcances de OAuth para solicitar (opcional)

> Si encuentra errores de alcance de OAuth, utilice una matriz vacía: `"oauthScopes": []`

#### 3. Configuración del agente

El campo `mcpServers` especifica a qué servidores MCP tiene acceso un agente personalizado:

```json
{
  "name": "myagent",
  "description": "My special agent",
  "mcpServers": {
    "fetch": {
      "command": "fetch3.1",
      "args": []
    }
  },
  "includeMcpJson": false
}
```

> `includeMcpJson: true` le da al agente acceso a todos los servidores MCP definidos en las configuraciones a nivel de usuario y espacio de trabajo, además de aquellos en el campo `mcpServers` del agente.

---

### Solución de problemas

#### Errores de validación de herramientas

Verifique que el servidor MCP esté ejecutándose y sea accesible. Consulte la documentación del servidor para conocer la configuración requerida.

#### Advertencias de descripción grande

Algunos servidores MCP proporcionan descripciones de herramientas muy extensas. Esto puede afectar el rendimiento. Considere utilizar un servidor más específico o herramientas de filtrado si están disponibles.

---

### Recursos adicionales

- [Registro del servidor MCP →](https://kiro.dev/docs/cli/mcp/registry/)
- [Ejemplos de MCP →](https://kiro.dev/docs/cli/mcp/examples/)
- [Seguridad de MCP →](https://kiro.dev/docs/cli/mcp/security/)

---

*📂 Capítulo: **MCP > Registry***

## Registro MCP

> **Fuente:** [kiro.dev/docs/cli/mcp/examples/](https://kiro.dev/docs/cli/mcp/examples/)

---

### Servidores MCP disponibles

#### Servidor de documentación de AWS

Proporciona acceso a la documentación de AWS, capacidades de búsqueda y recomendaciones.

**Capacidad:**
- Buscar documentación de AWS en todos los servicios
- Leer páginas de documentación en formato Markdown
- recomendaciones Obtener contenido relacionado

**Configuración (macOS/Linux):**
```json
{
  "mcpServers": {
    "docs-aws": {
      "comando": "uvx",
      "args": ["awslabs.aws-documentation-mcp-server@latest"],
      "entorno": { "FASTMCP_LOG_LEVEL": "ERROR" },
      "deshabilitado": falso
    }
  }
}
```

**Configuración (Windows):**
```json
{
  "mcpServers": {
    "docs-aws": {
      "comando": "uv",
      "args": ["herramienta", "ejecutar", "--from", "awslabs.aws-documentation-mcp-server@latest", "awslabs.aws-documentation-mcp-server.exe"],
      "env": { "FASTMCP_LOG_LEVEL": "ERROR" }
    }
  }
}
```

**Uso:**
```
Busque en la documentación de AWS las políticas del depósito S3
Lea la documentación de las URL de la función AWS Lambda
Encuentre contenido relacionado con las definiciones de tareas de AWS ECS
```

---

#### Servidor MCP de GitHub

Permite interactuar con repositorios, issues y pull request de GitHub.

**Configuración:**
```json
{
  "mcpServers": {
    "github": {
      "comando": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_PERSONAL_ACCESS_TOKEN": "<token>" }
    }
  }
}
```
Alcances de token requeridos: `repo`, `user`.

---

#### Servidores de bases de datos

| Servidor | Descripción |
|---|---|
| Servidor MCP PostgreSQL | Consulta y gestión de bases de datos PostgreSQL |
| Servidor MCP MongoDB | Interacción con bases de datos MongoDB |

#### Herramientas de desarrollo

| Servidor | Descripción |
|---|---|
| Servidor Docker MCP | Gestión de contenedores e imágenes Docker |
| Servidor Kubernetes MCP | Interacción con clusters Kubernetes |

---

### Encontrar más servidores MCP

- [Registro MCP] (https://github.com/modelcontextprotocol/registry)
- [Organización GitHub MCP](https://github.com/modelcontextprotocol)
- Buscar `mcp-server` en npm o PyPI

---

### Creando un servidor personalizado

1. Elegí un lenguaje (Python, Node.js, etc.)
2. Implementá el protocolo MCP usando las librerías disponibles
3. Defini tus herramientas y sus capacidades
4. Empaquetá y distribuiré tu servidor

**Recursos:**
- [Especificación del protocolo MCP] (https://modelcontextprotocol.io/specification/2025-06-18)
- [Documentación oficial de MCP] (https://modelcontextprotocol.io/introduction)

---

*📂 Capítulo: **MCP > Examples***

## Ejemplos de MCP

> **Fuente:** [kiro.dev/docs/cli/mcp/examples/](https://kiro.dev/docs/cli/mcp/examples/)

---

### Servidor de documentación de AWS: configuración completa

#### Requisitos previos

```golpecito
##macOS/Linux
rizo -LsSf https://astral.sh/uv/install.sh | sh

##WindowsPowerShell
irm https://astral.sh/uv/install.ps1 | iex

## Instalar Python 3.10+
instalación uv python 3.10
```

#### Configuración

**Vía CLI:**
```golpecito
kiro-cli mcp agregar \
  --nombre "awslabs.aws-documentation-mcp-server" \
  --alcance global \
  --comando "uvx" \
  --args "awslabs.aws-documentation-mcp-server@latest" \
  --env "FASTMCP_LOG_LEVEL=ERROR" \
  --env "AWS_DOCUMENTATION_PARTITION=aws"
```

**Vía `mcp.json`:**
```json
{
  "mcpServers": {
    "docs-aws": {
      "comando": "uvx",
      "args": ["awslabs.aws-documentation-mcp-server@latest"],
      "entorno": { "FASTMCP_LOG_LEVEL": "ERROR" },
      "deshabilitado": falso,
      "aprobación automática": []
    }
  }
}
```

#### Uso
```
Busque en la documentación de AWS las políticas del depósito S3
Lea la documentación de las URL de la función AWS Lambda
Obtenga recomendaciones para definiciones de tareas de AWS ECS
```

---

### Servidor GitHub MCP: configuración completa

#### Capacidades
- Gestión de repositorios, issues y pull request.
- Búsqueda de código en GitHub
- Operaciones de sucursales y commits.

#### Configuración
```golpecito
kiro-cli mcp agregar \
  --nombre "github" \
  --comando "npx" \
  --args "-y @modelcontextprotocol/servidor-github" \
  --env "GITHUB_PERSONAL_ACCESS_TOKEN=<tu-token>"
```

#### Configuración
```json
{
  "mcpServers": {
    "github": {
      "comando": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_PERSONAL_ACCESS_TOKEN": "<token>" }
    }
  }
}
```

Alcances de token requeridos: `repo`, `user`.

#### Herramientas comunes
- `list_issues` — Listar issues de un repositorio
- `create_pull_request` — Crear un PR
- `search_code` — Buscar código

---

### Servidor HTTP MCP con OAuth

```json
{
  "mcpServers": {
    "http-server-with-oauth": {
      "type": "http",
      "url": "https://api.example.com/mcp",
      "oauth": {
        "redirectUri": "127.0.0.1:8080",
        "oauthScopes": ["read", "write"]
      }
    }
  }
}
```

Si encuentra errores de alcance de OAuth, use un array vacío: `"oauthScopes": []`

---

### Servidor MCP personalizado

#### Ejemplo de estructura (Python)
```pitón
desde mcp import Server, Herramienta

servidor = Servidor("mi-servidor-personalizado")

@servidor.herramienta()
def my_tool(consulta: str) -> str:
    """Describe lo que hace esta herramienta"""
    return f"Resultado de: {consulta}"
```

Ver la [especificación del protocolo MCP](https://modelcontextprotocol.io/specification/2025-06-18) para detalles.

---

*📂 Capítulo: **MCP > Security***

## Seguridad MCP

> **Fuente:** [kiro.dev/docs/cli/mcp/security/](https://kiro.dev/docs/cli/mcp/security/)

---

### Consideraciones de seguridad

#### Confianza y verificación
- Solo instala servidores MCP de **fuentes confiables**
- Revisará las descripciones de las herramientas y la documentación antes de instalar.
- Verifica avisos de seguridad y actualizaciones

#### Control de acceso
- Usamos principios de **mínimo privilegio** para los permisos del servidor
- Limitá el acceso al sistema de archivos a los directorios necesarios únicamente
- Restringí el acceso a la red donde sea posible
- Usamos variables de entorno para credenciales sensibles

#### Gestión de credenciales
- **Nunca** codifica claves API o tokens en archivos de configuración
- Usamos variables de entorno para datos sensibles.
- Rotá las credenciales regularmente
- Almacená credenciales de forma segura usando el llavero del sistema

#### Seguridad de la red
- Usa HTTPS para servidores remotos MCP
- Verifica certificados SSL/TLS
- Sé cauteloso con servidores que requieren acceso amplio a la red
- Monitoreá el tráfico de red para actividad inusual

#### Monitoreo y Auditoría
- Revisará los registros del servidor MCP periódicamente
- Monitoreá comportamientos inesperados
- Llevá registro de los servidores instalados y sus permisos
- Elimina servidores no usados o no confiables rápidamente

---

### Seguridad de configuración

```golpecito
## Usamos variables de entorno para datos sensibles
exportar MCP_API_KEY="tu-clave-segura"
exportar DATABASE_URL="tu-cadena-de-conexión"

## Configurará el servidor MCP con variables de entorno
kiro-cli mcp agregar mi-servidor --env MCP_API_KEY --env DATABASE_URL
```

**`mcp.json` — forma correcta:**
```json
{
  "mcpServers": {
    "mi-servidor": {
      "comando": "comando-mi-servidor",
      "entorno": {
        "API_KEY": "$MCP_API_KEY"
      }
    }
  }
}
```

> ⚠️ Nunca comités archivos de configuración con claves API codificadas. Agregue `mcp.json` a `.gitignore` si contiene datos sensibles.

---

### Resumen de mejores prácticas

| Práctica | Descripción |
|---|---|
| Fuentes confiables | Solo instalar servidores verificados |
| Variables de entorno | Para todas las credenciales |
| Mínimo privilegio | Solo los permisos necesarios |
| Monitoreo activo | Revisar registros periódicamente |
| Removedor no usado | Eliminar servidores obsoletos |
| Usar HTTPS | Para servidores remotos |

---

*📂 Capítulo: **MCP > Best practices***

## Mejores prácticas de MCP

> **Fuente:** [kiro.dev/docs/cli/mcp/](https://kiro.dev/docs/cli/mcp/) | [kiro.dev/docs/cli/mcp/security/](https://kiro.dev/docs/cli/mcp/security/)

---

### Mejores prácticas de configuración

#### Utilice nombres descriptivos

```json
{
  "mcpServers": {
    "aws-docs": { ... },
    "github-integration": { ... },
    "project-db": { ... }
  }
}
```

Usá nombres descriptivos que reflejan el propósito del servidor.

#### Alcance apropiado

| Ámbito | Cuándo usarlo |
|---|---|
| **Global** (`~/.kiro/settings/mcp.json`) | Servidores que usamos en todos los proyectos (AWS docs, GitHub) |
| **Proyecto** (`.kiro/settings/mcp.json`) | Servidores específicos del proyecto (DB local, API interna) |
| **Agente** (en el JSON del agente) | Servidores exclusivos de un flujo de trabajo específico |

#### Establecer tiempos de espera adecuados

```json
{
  "mcpServers": {
    "slow-server": {
      "command": "slow-command",
      "args": [],
      "timeout": 300000
    }
  }
}
```

Aumente el tiempo de espera para servidores que tardan en iniciarse.

---

### Gestión de herramientas

#### Use `allowedTools` para operaciones comunes

```json
{
  "allowedTools": ["@aws-docs/search_documentation", "@aws-docs/read_documentation"]
}
```

Pre-aprobá herramientas de uso frecuente para reducir interrupciones.

#### Resolver conflictos de nombres con alias

```json
{
  "toolAliases": {
    "@github-mcp/get_issues": "github_issues",
    "@gitlab-mcp/get_issues": "gitlab_issues"
  }
}
```

---

### Mejores prácticas de rendimiento

- **Deshabilitar servidores no usados**: Usá `"disabled": true` en lugar de eliminar la configuración
- **Limitar el número de servidores**: Cada servidor agrega sobrecarga — solo cargará los necesarios
- **Monitorear descripciones grandes**: Si una herramienta tiene descripción >10,000 caracteres, puede afectar el rendimiento
- **Usar `includeMcpJson: false`** en agentes que no necesitan acceso a todos los servidores globales

---

### Flujo de trabajo de desarrollo

```golpecito
## 1. Agregar un nuevo servidor
kiro-cli mcp agregar --nombre mi-servidor --comando mi-comando --alcance global

## 2. Listar servidores configurados
lista de mcp de kiro-cli

## 3. Verificar que las herramientas están disponibles (en chat)
/herramientas

## 4. Ver registros de MCP para solucionar problemas
## Panel de salida → "Kiro - Registros de MCP"
```

---

### Prioridad de carga del servidor MCP

Cuando `includeMcpJson: true` en un agente:
1. Servidores del agente (`mcpServers` en el JSON del agente)
2. Servidores del proyecto (`.kiro/settings/mcp.json`)
3. Servidores globales (`~/.kiro/settings/mcp.json`)

En caso de conflicto de nombres, prevalece el servidor del agente.

Ver [Configuración →](../03_Chat/13_Configuration.md) para más detalles sobre prioridad de configuración.

---

*📂 Capítulo: **Steering***

## Steering - Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/steering/](https://kiro.dev/docs/cli/steering/)

---

Los archivos de Steering guían la IA de Kiro con el contexto específico del proyecto a través de documentos Markdown que definen sus estándares, arquitectura y convenciones.

---

### ¿Qué es el Steering?

Los archivos de Steering son documentos Markdown almacenados en `.kiro/steering/` que Kiro lee automáticamente durante las sesiones de chat. Proporcionan conocimiento específico del proyecto que da forma a la generación y el comportamiento del código de Kiro.

**Beneficios clave:**
- Calidad de código consistente en todas las sesiones.
- Aplicación automática de convenciones de equipo.
- Correcciones repetitivas reducidas
- Experiencia en un dominio específico

---

### Alcance del archivo de Steering

#### Steering del espacio de trabajo

Reside en `.kiro/steering/` en la raíz de tu espacio de trabajo. Aplicar solo a ese espacio de trabajo específico.

#### Steering global

Reside en `~/.kiro/steering/` en tu directorio de inicio. Aplicar a **todos** los espacios de trabajo.

> **Nota:** En caso de instrucciones contradictorias, **el Steering del espacio de trabajo tiene prioridad** sobre el Steering global.

#### Steering del equipo

Los archivos de Steering globales se pueden distribuir a equipos completos a través de soluciones MDM, políticas de grupo o descargar desde un repositorio central a `~/.kiro/steering`.

---

### Archivos de Steering fundamentales

Cree archivos de Steering fundamentales en `.kiro/steering/` (espacio de trabajo) o `~/.kiro/steering` (global):

| Archivo | Propósito |
|---|---|
| `producto.md` | Propósito del producto, usuarios objetivo, características clave y objetivos comerciales |
| `tecnología.md` | Marcos, bibliotecas, herramientas de desarrollo y limitaciones técnicas |
| `estructura.md` | Organización de archivos, convenciones de nomenclatura, patrones de importación y decisiones arquitectónicas |

Estos archivos básicos se incluyen en cada interacción de forma predeterminada.

---

### Creación de archivos de Steering personalizados

1. Cree un nuevo archivo `.md` en `.kiro/steering/`
2. Elija un nombre de archivo descriptivo (por ejemplo, `api-standards.md`)
3. Escriba su guía utilizando Markdown estándar y lenguaje natural.

---

### Steering con agentes personalizados

Cuando se utilizan [agentes personalizados](https://kiro.dev/docs/cli/custom-agents/creating), los archivos de Steering **no se incluyen automáticamente**. Agréguelos explícitamente a la configuración de "recursos" del agente:

```json
{
  "resources": ["file://.kiro/steering/**/*.md"]
}
```

Este patrón global garantiza que todos los archivos Markdown en su directorio de Steering se carguen cuando se utiliza el agente.

---

### Agentes.md

Kiro admite el estándar [AGENTS.md](https://agents.md/). Agregue archivos `AGENTS.md` a `~/.kiro/steering/` o a la carpeta raíz de su espacio de trabajo; **siempre se incluyen** automáticamente.

---

### Mejores prácticas

- **Mantenga los archivos enfocados**: un dominio por archivo
- **Utilice nombres claros**: `api-rest-conventions.md`, `testing-unit-patterns.md`
- **Incluir contexto**: explique *por qué* se tomaron las decisiones
- **Proporcione ejemplos**: use fragmentos de código y comparaciones antes/después
- **La seguridad es lo primero**: nunca incluya claves API ni datos confidenciales
- **Mantener regularmente**: trate los cambios de Steering como cambios de código

---

### Estrategias comunes de archivos de Steering

| Archivo | Contenido |
|---|---|
| `api-estándares.md` | Convenciones REST, formatos de respuesta de error, flujos de autenticación |
| `testing-standards.md` | Patrones de pruebas unitarias, estrategias de integración, mocks, cobertura |
| `código-convenciones.md` | Patrones de nombres, organización de archivos, decisiones arquitectónicas |
| `políticas-de-seguridad.md` | Requisitos de autenticación, validación de datos, codificación segura |
| `despliegue-flujo de trabajo.md` | Procedimientos de compilación, configuraciones del entorno, detalles de CI/CD |

---

*📂 Capítulo: **Agent Skills***

## Skills del agente

> **Fuente:** [kiro.dev/docs/cli/skills/](https://kiro.dev/docs/cli/skills/)

---

Los Agent Skills son paquetes portátiles de instrucciones que se activan automáticamente cuando tu solicitud coincide con su descripción. Son similares a los Steering Files pero **on-demand** — Kiro solo los carga cuando son necesarios.

---

### Cómo funcionan las skills

Al iniciar una sesión de chat, Kiro descubre las skills disponibles leyendo sus nombres y descripciones. Cuando tu solicitud coincide con la descripción de una skill, Kiro carga automáticamente las instrucciones completas y las sigue.

```
> Review this PR for security issues
[skill: pr-review activated]
I'll review the PR using the security checklist...
```

Las skills **se activan automáticamente** según tu solicitud. No hay comando de barra diagonal para invocarlos: Kiro decide cuándo una skill es relevante comparando tu solicitud contra las descripciones de las skills.

Para ver qué skills están disponibles en tu sesión actual:

```
> /context show
```

---

### Ubicaciones de skills

Las skills pueden almacenarse en dos lugares:

| Ubicación | Alcance |
|---|---|
| `.kiro/skills/` | **Espacio de trabajo** — Solo para ese proyecto |
| `~/.kiro/skills/` | **Global** — Disponible en todos los espacios de trabajo |

Cuando las skills comparten el mismo nombre, **las skills del espacio de trabajo tienen prioridad** sobre los globales.

#### Agente predeterminado

El agente por defecto (`kiro_default`) carga automáticamente todos los skills en `.kiro/skills/` y `~/.kiro/skills/`.

#### Agentes personalizados

Los agentes personalizados requieren que especifiques explícitamente las skills en su configuración usando el protocolo `skill://`:

```json
{
  "resources": ["skill://pr-review", "skill://cdk-deploy"]
}
```

---

### Creando una skill

Un Skill es una **carpeta** que contiene un archivo `SKILL.md`:

```
pr-review/
├── SKILL.md         # Requerido
└── references/      # Opcional
    └── checklist.md
```

#### Formato SKILL.md

El archivo empieza con **YAML frontmatter** seguido de instrucciones en Markdown:

```markdown
---
nombre: pr-revisión
Descripción: revise las pull requests para determinar la calidad del código, los problemas de seguridad y la cobertura de las pruebas. Úselo al revisar Pull Requests o preparar código para revisión.
---

### Revisar la lista de verificación
Al revisar una pull request:
1. Verifique vulnerabilidades, riesgos de inyección y secretos expuestos.
2. Verificar que se manejen los casos extremos y los modos de falla
3. Confirme que el nuevo código tenga las pruebas adecuadas.
4. Asegúrese de que las variables y funciones tengan nombres claros

### Problemas comunes a señalar
- Credenciales codificadas o claves API
- Falta validación de entrada
- Rechazos de promesas no controlados
- Declaraciones Console.log dejadas en el código de producción.
```

#### Campos frontales

| Campo | Descripción |
|---|---|
| `nombre` | Identificador único del Skill |
| `descripción` | **Crítico** — Determina cuándo se activa. Incluir palabras clave y acciones específicas. |

#### Archivos de referencia

Para documentación extensa, use una carpeta `references/`:

```
aws-deployment/
├── SKILL.md
└── references/
    ├── ecs-guide.md
    └── troubleshooting.md
```

Referencia los archivos desde `SKILL.md`:

```markdown
For ECS deployments, follow the guide in `references/ecs-guide.md`.
```

Kiro carga los archivos de referencia **solo cuando las instrucciones lo indican**.

---

### Ejemplo completo: skill de implementación de CDK

```
cdk-deploy/
├── SKILL.md
└── references/
    └── stack-patterns.md
```

**SKILL.md:**
```markdown
---
nombre: implementación de cdk
Descripción: Implemente pilas de AWS CDK con las mejores prácticas. Úselo al implementar infraestructura, ejecutar cdk implementar o solucionar problemas de CDK.
---

### Flujo de trabajo de implementación
1. Ejecute `cdk synth` para validar las plantillas antes de implementarlas.
2. Utilice `cdk diff` para obtener una vista previa de lo que cambiará
3. Ejecute `cdk implementar` y revise los cambios de IAM

### Comprobaciones previas al despliegue
- Verifique que las credenciales de AWS estén configuradas para la cuenta de destino
- Verificar que la versión CDK coincida con los requisitos del proyecto.
- Revise `references/stack-patterns.md` para conocer patrones específicos del entorno

### Procedimiento de reversión
Si la implementación falla:
1. Verifique la consola de CloudFormation para ver el error específico.
2. Ejecute `cdk destroy` solo si la pila está en un estado fallido
3. Solucione el problema y vuelva a implementar
```

**Uso:**
```
> Implementar mi pila CDK en preparación
[skill: cdk-deploy activado]
Seguiré el flujo de trabajo de implementación. Primero, déjame sintetizar las plantillas...
```

---

### Mejores prácticas

- **Descripciones precisas** — La descripción determina la activación. Ejemplos:
  - ✅ `Revisar las pull requests para detectar vulnerabilidades de seguridad. Úselo al revisar las Pull Requests.`
  - ❌ `Ayuda con la revisión del código`
- **SKILL.md accionable** — Poné el material de referencia detallado en `references/`
- **Elegí el alcance correcto** — Skills globales para flujos de trabajo personales; espacio de trabajo para procedimientos de equipo
- **Versión de control** — Commitá `.kiro/skills/` a tu repositorio para que todo el equipo comparta los flujos de trabajo

---

### Relacionado

- [Steering →](./06_Steering.md) — Contexto y convenciones del proyecto
- [Agentes personalizados →](./04_Custom%20agents/) — Configuración de agentes y recursos
- [ACP →](./08_ACP.md) — Protocolo de cliente agente

---

*📂 Capítulo: **Hooks***

## Hooks — Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/hooks/](https://kiro.dev/docs/cli/hooks/)

---

Los hooks le permiten ejecutar comandos personalizados en puntos específicos durante el ciclo de vida del agente y la ejecución de la herramienta. Le permiten validar acciones automáticamente, inyectar contexto o ejecutar tareas de posprocesamiento.

---

### Definición de hooks

Los enlaces se definen en el archivo de configuración del agente. Consulte la [Referencia de configuración del agente](https://kiro.dev/docs/cli/custom-agents/configuration-reference#hooks-field) para obtener la sintaxis completa.

---

### Evento de gancho

Los hooks reciben un evento de gancho en **formato JSON a través de STDIN**:

```json
{ "hook_event_name": "agentSpawn", "cwd": "/current/working/directory" }
```

Para los hooks relacionados con herramientas, se incluyen campos adicionales:
- `tool_name` — Nombre de la herramienta que se está ejecutando
- `tool_input` — Parámetros específicos de la herramienta
- `tool_response` — Resultados de ejecución de la herramienta *(solo PostToolUse)*

---

### Salida de gancho

| Código de salida | Comportamiento |
|---|---|
| `0` | Hook tuvo éxito. STDOUT se captura pero no se muestra al usuario. |
| `2` | *(Solo PreToolUse)* Bloquear la ejecución de la herramienta. STDERR se devuelve al LLM. |
| Otro | El gancho falló. STDERR se muestra como una advertencia para el usuario. |

---

### Coincidencia de herramientas

Utilice el campo `matcher` para especificar a qué herramientas se aplica el gancho:

| Emparejador | Partidos |
|---|---|
| `"fs_write"` o `"escribir"` | Herramienta de escritura |
| `"fs_read"` o `"read"` | Herramienta de lectura |
| `"execute_bash"` o `"shell"` | Ejecución del comando Shell |
| `"use_aws"` o `"aws"` | Herramienta AWS CLI |
| `"@git"` | Todas las herramientas del servidor git MCP |
| `"@git/estado"` | Herramienta específica del servidor git MCP |
| `"*"` | Todas las herramientas (integradas y MCP) |
| `"@integrado"` | Sólo todas las herramientas integradas |
| *(sin igualador)* | Se aplica a todas las herramientas |

---

### Tipos de gancho

#### AgenteSpawn

Se ejecuta cuando se activa el agente. No se proporciona contexto de herramienta.

```json
{ "hook_event_name": "agentSpawn", "cwd": "/actual/trabajo/directorio" }
```
- Salir `0`: STDOUT se agrega al contexto del agente
- Otro: muestra la advertencia STDERR al usuario

---

#### Aviso de usuarioEnviar

Se ejecuta cuando el usuario envía un mensaje. La salida se agrega al contexto de la conversación.

```json
{ "hook_event_name": "userPromptSubmit", "cwd": "/current/working/directory", "prompt": "mensaje de entrada del usuario" }
```
- Salir `0`: STDOUT se agrega al contexto del agente
- Otro: muestra la advertencia STDERR al usuario

---

#### Uso previo de la herramienta

Se ejecuta **antes** de la ejecución de la herramienta. Puede validar y bloquear el uso de herramientas.

```json
{
  "hook_event_name": "preToolUse",
  "cwd": "/actual/trabajo/directorio",
  "nombre_herramienta": "leer",
  "tool_input": { "operaciones": [{ "modo": "Línea", "ruta": "/docs/hooks.md" }] }
}
```
- Salir `0`: Permitir la ejecución de la herramienta
- Salir `2`: Bloquear la ejecución de la herramienta, devolver STDERR a LLM
- Otro: muestra la advertencia STDERR, permite la ejecución de la herramienta

---

#### Uso de la herramienta posterior

Se ejecuta **después** de la ejecución de la herramienta con acceso a los resultados de la herramienta.

```json
{
  "hook_event_name": "postToolUse",
  "nombre_herramienta": "leer",
  "tool_input": {...},
  "tool_response": { "éxito": verdadero, "resultado": ["..."] }
}
```
- Salir `0`: Hook exitoso
- Otro: Mostrar advertencia STDERR (la herramienta ya se ejecutó)

---

#### Detener

Corre cuando el asistente termina de responder (fin de cada turno). Útil para el posprocesamiento: compilación, prueba, formateo o limpieza.

```json
{ "hook_event_name": "stop", "cwd": "/current/working/directory" }
```

> Nota: Los hooks de parada no utilizan comparadores ya que no se relacionan con herramientas específicas.

---

#### Ejemplo de herramienta MCP

Para las herramientas MCP, el nombre de la herramienta incluye el formato de espacio de nombres completo:

```json
{
  "hook_event_name": "preToolUse",
  "tool_name": "@postgres/query",
  "tool_input": { "sql": "SELECT * FROM orders LIMIT 10;" }
}
```

---

### Se acabó el tiempo

El tiempo de espera predeterminado es **30 segundos** (30 000 ms). Configure con el campo `timeout_ms` en la configuración de su agente.

---

### Almacenamiento en caché

Los resultados del enlace exitoso se almacenan en caché según `cache_ttl_segundos`:

| Valor | Comportamiento |
|---|---|
| `0` | Sin almacenamiento en caché (predeterminado) |
| `> 0` | Almacenar en caché los resultados exitosos durante segundos específicos |
| — | Los hooks `AgentSpawn` nunca se almacenan en caché |

---

*📂 Capítulo: **ACP***

## Protocolo de cliente agente (ACP)

> **Fuente:** [kiro.dev/docs/cli/acp/](https://kiro.dev/docs/cli/acp/)

---

ACP (Agent Client Protocol) es un protocolo estandarizado para la comunicación agente-editor, similar a cómo el Language Server Protocol (LSP) estandarizó la integración del servidor de idiomas. Los agentes que implementan ACP funcionan con cualquier editor compatible y los editores que admiten ACP obtienen acceso a todos los agentes compatibles con ACP.

---

### ¿Qué es ACP?

Los agentes y editores de codificación de IA están estrechamente vinculados sin un estándar. Cada editor debe crear integraciones personalizadas para cada agente, lo que genera una sobrecarga de integración, compatibilidad limitada y dependencia del desarrollador.

ACP resuelve esto proporcionando un protocolo estandarizado. Kiro CLI implementa ACP para que pueda usarse como agente de IA en cualquier editor compatible con ACP (JetBrains, Zed, etc.).

---

### Inicio rápido

Ejecute Kiro como agente ACP:
```golpecito
kiro-cli acp
```

Utilice una configuración de agente específica:
```golpecito
kiro-cli acp --agente mi-agente
```

El agente se comunica a través de **stdin/stdout** usando **JSON-RPC 2.0**. Configure su editor para generar este comando.

---

### Configuración del editor

#### General

Utilice la **ruta completa** a `kiro-cli` en la configuración de su editor. Los IDE a menudo no heredan la RUTA de su shell, por lo que es posible que no se encuentren comandos como `kiro-cli`.

Encuentra el camino:
```golpecito
cual kiro-cli
## Comúnmente: ~/.local/bin/kiro-cli en Linux/macOS
```

#### IDE de JetBrains

Configure a través de la configuración del **complemento JetBrains AI**. Agregue Kiro CLI como agente compatible con ACP utilizando la ruta completa.

#### Zed

Configure en `~/.config/zed/settings.json` en la sección `assistant`. Establezca el comando en la ruta completa de `kiro-cli acp`.

#### Otros editores

Cualquier editor que admita el protocolo ACP puede utilizar Kiro CLI. Consulte la documentación del editor específico para configurar los agentes ACP.

---

### Métodos ACP admitidos

Kiro CLI implementa la especificación ACP que incluye:
- **Protocolo central**: gestión de sesiones, selección de modelos y transmisión de respuestas
- **Capacidades del agente**: acceso a herramientas, gestión de contexto y estado de conversación
- **Actualizaciones de sesiones**: transmisión en tiempo real de las respuestas de los agentes

---

### Extensiones Kiro

Kiro extiende ACP con métodos personalizados (con el prefijo `_kiro.dev/` según la especificación de ACP) para exponer características específicas de Kiro:

- [Comandos de barra diagonal] (https://kiro.dev/docs/cli/reference/slash-commands)
- [eventos del servidor MCP] (https://kiro.dev/docs/cli/mcp)
- [Compactación de contexto](https://kiro.dev/docs/cli/chat#context-management)

Los clientes que no admiten estas extensiones pueden ignorarlas con seguridad: son mejoras opcionales.

> Nota: Estas extensiones son **experimentales** y están sujetas a cambios en futuras versiones.

---

### Almacenamiento de sesiones

Las sesiones se almacenan localmente y se pueden reanudar. El ID de sesión se incluye en las respuestas de ACP para permitir a los clientes hacer referencia a sesiones específicas.

### Registro

Utilice el indicador `--log-level` para controlar la detalle del registro cuando se ejecuta en modo ACP. Los registros se escriben en stderr para evitar interferir con la comunicación JSON-RPC en stdout.

---

*📂 Capítulo: **Autocomplete***

## Finalizaciones y Autocompletar

> **Fuente:** [kiro.dev/docs/cli/autocomplete/](https://kiro.dev/docs/cli/autocomplete/)

---

Kiro CLI proporciona sugerencias y completaciones de comandos impulsadas por IA para cientos de herramientas CLI populares, lo que hace que la línea de comandos funcione más rápido y con mayor precisión.

---

### Menú desplegable de autocompletar

El menú desplegable de autocompletar aparece a la **derecha del cursor** al escribir comandos y muestra las opciones, subcomandos y argumentos disponibles que puede seleccionar usando las teclas de flecha.

#### Usando Autocompletar

- Comience a escribir un comando
- El menú desplegable aparece automáticamente con sugerencias.
- Utilice **teclas de flecha** para navegar
- Presione **Tab** o **Enter** para aceptar una sugerencia.

#### Configuración

El comportamiento de autocompletar se puede configurar en la configuración de Kiro CLI. Consulte la [referencia de configuración de CLI](https://kiro.dev/docs/cli/reference/) para conocer las opciones disponibles.

---

### Sugerencias en línea

Las sugerencias en línea aparecen como **"texto fantasma"** gris directamente en la línea de comando a medida que escribe. Esta función funciona independientemente del menú desplegable.

#### Uso de sugerencias en línea

- Escriba el comienzo de un comando
- Aparece un texto fantasma que muestra la finalización prevista.
- Presione **Tab** para aceptar la sugerencia completa
- Presione **→** (flecha derecha) para aceptar palabra por palabra
- Continúe escribiendo para descartar y anular la sugerencia.

#### Gestión de sugerencias en línea

Active o desactive las sugerencias en línea en la configuración de su shell o en la configuración de CLI.

---

### Herramientas compatibles

Kiro CLI proporciona complementos para cientos de herramientas populares, entre las que se incluyen:

**Herramientas populares:** `git`, `docker`, `kubectl`, `npm`, `yarn`, `pip`, `cargo`, `make`, `terraform`, `aws`

**Herramientas de lenguaje:** `node`, `python`, `go`, `ruby`, `java`, `rustc`, `gcc`, `mvn`, `gradle`

**Herramientas del sistema:** `ls`, `cd`, `grep`, `find`, `curl`, `ssh`, `chmod`, `systemctl`

---

### Solución de problemas

#### Autocompletar no funciona

- Verifique que Kiro CLI esté instalado correctamente y en su RUTA
- Reinicia tu terminal después de la instalación
- Verifique que la integración de shell esté habilitada en su perfil (`.bashrc`, `.zshrc`, etc.)

#### Problemas de sugerencias en línea

- Asegúrese de que su emulador de terminal admita las secuencias de escape requeridas
- Verifique que las sugerencias en línea estén habilitadas en su configuración Kiro CLI

---

*📂 Capítulo: **Experimental > Knowledge management***

## Gestión del conocimiento

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#knowledge-management)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

### Descripción general

La Gestión del Conocimiento habilita almacenamiento y recuperación de contexto persistente a través de sesiones de chat, con capacidades de **búsqueda semántica**.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableKnowledge verdadero
```

**Comando:** `/conocimiento`

---

### Características

- Almacenamiento de archivos, directorios y contenido de texto.
- Búsqueda semántica para mejor recuperación de contexto
- Base de conocimiento persistente entre sesiones.
- Aislamiento de conocimiento por agente

---

### Uso de la gestión del conocimiento

```
/knowledge add ./docs          # Indexar directorio
/knowledge add ./README.md     # Indexar archivo específico
/knowledge search "auth flow"  # Búsqueda semántica
/knowledge list                # Ver todo el conocimiento indexado
/knowledge delete <id>         # Eliminar un item
```

---

### Integración con agentes personalizados

Podés usar bases de conocimiento en los recursos de un agente:

```json
{
  "resources": [{
    "type": "knowledgeBase",
    "source": "file://./docs",
    "name": "ProjectDocs",
    "description": "Project documentation",
    "indexType": "best",
    "autoUpdate": true
  }]
}
```

| Campo | Opciones | Predeterminado |
|---|---|---|
| `tipo de índice` | `"best"` (más preciso) / `"fast"` (más rápido) | `"mejor"` |
| `actualización automática` | `verdadero` / `falso` | `falso` |

---

### Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos completos de gestión del conocimiento →](https://kiro.dev/docs/cli/experimental/knowledge-management)

---

*📂 Capítulo: **Experimental > Tangent mode***

## Modo tangente

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#tangent-mode)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

### Descripción general

Tangent Mode permite crear **puntos de control de conversación** para explorar temas secundarios sin interrumpir el flujo principal de la conversación.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableTangentMode verdadero
```

**Activar:** `/tangente` o `Ctrl+T`

---

### Características

- Crear puntos de control de conversación.
- Explorar temas tangenciales
- Volver al hilo principal de conversación
- Preservar el contexto de la conversación.

---

### Cómo funciona

```
> Estoy implementando autenticación con JWT...
> /tangent # o Ctrl+T — crea un punto de control aquí

[tangente] > ¿Cuál es la diferencia entre RS256 y HS256?
[tangente] > ¿Cuándo usar cada uno?

> /tangent # vuelve al punto de control anterior

> Continuando con JWT... (contexto preservado)
```

---

### Casos de uso

- Hacer preguntas de contexto sin perder el hilo principal
- Explorar alternativas antes de comprometerse con un enfoque
- Investigar un error sin contaminar la conversación principal
- Aprender sobre una tecnología mientras trabajas en otra tarea

---

### Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos del modo tangente completo →](https://kiro.dev/docs/cli/experimental/tangent-mode)

---

*📂 Capítulo: **Experimental > TODO lists***

## Listas de tareas pendientes

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#todo-lists)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

### Descripción general

TODO Lists permite a Kiro crear y modificar listas de tareas automáticamente durante las sesiones de chat, con comandos para verlas y gestionarlas.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableTodoList verdadero
```

**Comando:** `/todo`

---

### Características

- Kiro crea automáticamente TODOs cuando es apropiado
- Ver, gestionar y eliminar TODOs
- Retomar listas de TODO existentes
- Persistidas entre sesiones de chat.

---

### Uso

```
## Kiro crea TODOs automáticamente al planear tareas complejas
> Implementar la autenticación de usuarios con JWT

##manual de gestión
/todo list # Ver todos los TODOs
/todo show <id> # Ver detalles de un TODO
/todo eliminar <id> # Eliminar un TODO
/todo resume <id> # Retomar un TODO existente
```

---

### Flujo de ejemplo

```
> Implementar una API REST con autenticación de usuario, catálogo de productos y gestión de pedidos

Kiro crea automáticamente:
☐ 1. Configurar la estructura y las dependencias del proyecto.
☐ 2. Implementar la autenticación de usuario (JWT)
☐ 3. Crear puntos finales del catálogo de productos
☐ 4. Construir un sistema de gestión de pedidos
☐ 5. Agregar pruebas unitarias

> /lista de tareas pendientes
[TODO 1234] "Implementación de API REST" - 0/5 completo
```

---

### Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos completos de listas de TODO →](https://kiro.dev/docs/cli/experimental/todo-lists)

---

*📂 Capítulo: **Experimental > Thinking tool***

## Herramienta de pensamiento

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#thinking-tool)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

### Descripción general

El Thinking Tool muestra el **proceso de pensamiento de la IA** para problemas complejos, con procesos de pensamiento paso a paso visibles para el usuario.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enablePensando verdadero
```

---

### Características

- Proceso de toma de decisiones transparente
- Visualización del razonamiento paso a paso
- Útil para depuración y aprendizaje
- Mejor comprensión de las conclusiones del agente

---

### Salida de ejemplo

```
> ¿Por qué mi API devuelve 401 incluso con un token válido?

[pensando]
1. El usuario tiene un token válido pero obtiene 401.
2. Posibles causas:
   - Formato del token incorrecto (falta el prefijo del portador)
   - Token caducado
   - Algoritmo de firma incorrecto
   - El nombre del encabezado no coincide
3. Es necesario verificar: configuración del middleware, lógica de validación del token
[/pensando]

Al observar su código, es probable que el problema esté en el middleware...
```

---

### Casos de uso

- **Complejo de depuración** — Ver cómo el agente analiza el problema
- **Aprendizaje** — Entender el razonamiento detrás de las decisiones
- **Validación** — Verificar que el agente está considerando los factores correctos
- **Arquitectura** — Evaluar trade-offs en decisiones de diseño

---

### Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos completos de la herramienta de pensamiento →](https://kiro.dev/docs/cli/experimental/thinking)

---

*📂 Capítulo: **Experimental > Checkpointing***

## Puntos de control

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#checkpointing)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

### Descripción general

Checkpointing habilita **instantáneas de sesión** para rastrear cambios de archivos usando comandos tipo Git. Funciona mediante un "shadow git repo" que captura el estado de los archivos.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableCheckpoint verdadero
```

**Comando:** `/punto de control`

---

### Características

- Instantáneas de cambios de archivos en un repositorio de Shadow Git
- Listar, expandir, comparar y restaurar puntos de control
- El historial de conversación se revierte al restaurar.
- Se activa automáticamente en repositorios Git
- Manual de iniciación para directorios sin git

---

### Comandos

```bash
/checkpoint list                  # Ver todos los checkpoints
/checkpoint expand <tag>          # Ver detalles de un checkpoint
/checkpoint diff <tag1> [tag2]    # Comparar checkpoints
/checkpoint restore [<tag>]       # Restaurar al checkpoint
/checkpoint clean                 # Eliminar el shadow repo de la sesión
```

---

### Ejemplo de flujo de trabajo

```
> Implementar autenticación de usuario

Kiro hace varios cambios de archivos...

> /lista de puntos de control
CHECKPOINT-001 "Implementación de autenticación inicial" 5 archivos modificados
CHECKPOINT-002 "Middleware JWT agregado" 3 archivos modificados

> /diferencia punto de control CHECKPOINT-001 CHECKPOINT-002
## Muestra los cambios entre puntos de control.

## Si algo salió mal:
> /restaurar punto de control CHECKPOINT-001
## Restaura los archivos Y el historial de conversación
```

---

### Habilitar automáticamente en repositorios de Git

En repositorios Git, los puntos de control pueden activarse automáticamente al iniciar una sesión. Para directorios sin git, la inicialización es manual.

---

### Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos completos sobre puntos de control →](https://kiro.dev/docs/cli/experimental/checkpointing)

---

*📂 Capítulo: **Experimental > Delegate***

## Delegado

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#delegate)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

### Descripción general

Delegate permite lanzar y gestionar **procesos de tareas asíncronos**, ejecutando sesiones de chat de Kiro con agentes específicos en paralelo, en segundo plano.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableDelegate verdadero
```

---

### Características

- Lanzar tareas en segundo plano usando lenguaje natural.
- Ejecutar sesiones de chat paralelas con agentes específicos
- Monitorear el progreso de las tareas de forma independiente.
- Flujo de aprobación del agente para seguridad

---

### Uso

```
## Lanzar una tarea en segundo plano con lenguaje natural
> ¿Puedes crear una tarea en segundo plano para analizar el rendimiento de nuestros puntos finales API?

## El agente pide aprobación, luego ejecuta en segundo plano
✔ Lanzamiento de tarea en segundo plano: Análisis de rendimiento de API

## Verificar el estado
> Verificar el estado de mi tarea de análisis de API

## Ver resultados
> Muéstrame los resultados del análisis de antecedentes.
```

---

### Casos de uso

- **Análisis de código largo** — Ejecutar en segundo plano mientras sigues trabajando
- **Tests extensos** — Correr suites de tests sin bloquear la sesión
- **Generación de documentación** — Generar docs de Múltiples archivos en paralelo
- **Migraciones** — Tareas pesadas que llevan mucho tiempo

---

### Seguridad

El delegado incluye un **flujo de aprobación** antes de ejecutar cada tarea. Revise siempre qué va a hacer el agente antes de aprobar.

---

### Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos completos del delegado →](https://kiro.dev/docs/cli/experimental/delegate)

---

*📂 Capítulo: **Experimental > TUI v2***

## TUI v2

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

### Descripción general

**TUI v2** es la próxima generación de la interfaz de usuario de terminal (Text User Interface) de Kiro CLI, actualmente en desarrollo activo.

---

### Gestión de funciones experimentales

Todas las características experimentales (incluido TUI v2) se gestionan con el comando `/experiment`:

```golpecito
## Ver menú interactivo
/experimento

## Ver estado actual de todos los experimentos
lista de configuraciones de kiro-cli | grep -yo habilito

## Habilitar características individuales
configuración de kiro-cli chat.enableKnowledge verdadero
configuración de kiro-cli chat.enableTangentMode verdadero
configuración de kiro-cli chat.enableTodoList verdadero
configuración de kiro-cli chat.enablePensando verdadero
configuración de kiro-cli chat.enableCheckpoint verdadero
configuración de kiro-cli chat.enableContextUsageIndicator verdadero
configuración de kiro-cli chat.enableDelegate verdadero
```

---

### Porcentaje de uso del contexto

Una característica relacionada es el **indicador de uso de contexto** — muestra el porcentaje de ventana de contexto usado en el aviso:

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableContextUsageIndicator verdadero
```

| Color | Uso |
|---|---|
| 🟢 Verde | < 50% |
| 🟡 Amarillo | 50-89% |
| 🔴Rojo | 90-100% |

Ejemplo de indicador con indicador: `[rust-agent] 6% >`

---

### Soporte de búsqueda difusa

Todos los comandos experimentales están disponibles en búsqueda difusa (`Ctrl+S`):

- `/experiment` — Gestionar características experimentales
- `/knowledge` — Base de conocimientos (cuando está habilitado)
- `/todo` — Listas TODO (cuando está habilitado)
- `/tangent` — Alternar modo tangente (cuando está habilitado)
- `/checkpoint` — Comandos de punto de control (cuando está habilitado)

---

### Mejores prácticas

1. **Tesear en entornos seguros** — Probar características experimentales en proyectos no críticos primero
2. **Dar feedback** — Reportar problemas y sugerencias con `kiro issues`
3. **Mantenerse actualizado** — Revisar notas de la versión para cambios en características experimentales
4. **Entender limitaciones** — Leer la documentación individual para conocer temas conocidos
5. **Tener copias de seguridad** — Algunas características modifican archivos (puntos de control, listas de TODO)

---

### Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)

---

*📂 Capítulo: **Code intelligence***

## Inteligencia de código

> **Fuente:** [kiro.dev/docs/cli/code-intelligence/](https://kiro.dev/docs/cli/code-intelligence/)

---

Code Intelligence proporciona una comprensión profunda del código mediante el uso de Tree-sitter (integrado) y la integración LSP opcional para la búsqueda de símbolos, la coincidencia de patrones y la exploración de la base de código, todo sin salir de su terminal.

---

### Idiomas admitidos

Bash, C, C++, C#, Elixir, Go, Java, JavaScript, Kotlin, Lua, PHP, Python, Ruby, Rust, Scala, Swift, TSX, TypeScript

---

### Funciones integradas *(no se requiere LSP)*

| Característica | Descripción |
|---|---|
| **Búsqueda de símbolos** | Buscar funciones, clases y métodos por nombre (coincidencia difusa) |
| **Símbolos del documento** | Listar todos los símbolos en un archivo |
| **Búsqueda de símbolos** | Busque símbolos específicos por nombre exacto |
| **Búsqueda de patrones** | Búsqueda de códigos estructurales basada en AST |
| **Reescritura de patrón** | Transformaciones de código automatizadas utilizando patrones AST |
| **Descripción general del código base** | Descripción general de la estructura base del código de alto nivel |
| **Mapa de código base** | Explorar la estructura del directorio y la organización del código |

---

### Descripción general de la base de código

Obtenga una descripción completa de cualquier espacio de trabajo en segundos:

```bash
/code overview
```

Centrarse en un directorio específico:
```golpecito
/descripción general del código ./src/components
```

Utilice `--silent` para obtener resultados más limpios cuando profundice en un paquete:
```golpecito
/ descripción general del código --silencioso
```

Ideal para: incorporación a nuevas bases de código, preguntas y respuestas sobre la estructura del proyecto y comprensión rápida de paquetes desconocidos.

---

### Generación de documentación

Genere documentación para su código base con una sesión interactiva:

```bash
/code summary
```

Elija el formato de salida:
- **AGENTS.md** — Documentación para agentes de IA que trabajan con su código base
- **README.md** — Documentación estándar del proyecto
- **CONTRIBUTING.md** — Directrices para contribuyentes

---

### Búsqueda y reescritura de patrones

Búsqueda y transformación de código estructural basada en AST. Busque y modifique código por estructura, no solo por texto.

#### Metavariables

Utilice metavariables (por ejemplo, `$FUNC`, `$ARG`) en patrones para que coincidan con cualquier expresión de ese tipo.

#### Ejemplos de búsqueda de patrones

```bash
## Find all function calls with specific patterns
/code search "console.log($MSG)"
```

#### Ejemplos de reescritura de patrones

```bash
## Replace deprecated API calls
/code rewrite "oldAPI($ARG)" --to "newAPI($ARG)"
```

---

### Integración LSP *(Opcional)*

Las funciones integradas de cuidado de árboles funcionan desde el primer momento. Ejecute `/code init` solo si desea funciones LSP mejoradas.

> La inteligencia del código se configura por espacio de trabajo: cada proyecto mantiene su propia configuración de LSP de forma independiente.

```bash
/code init
```

**Operaciones adicionales impulsadas por LSP:**

| Característica | Descripción |
|---|---|
| **Buscar referencias** | Localice todos los usos de un símbolo en una posición |
| **Ir a la definición** | Navegue hasta donde se define un símbolo |
| **Cambiar nombre del símbolo** | Cambiar el nombre de los símbolos en todo el código base |
| **Obtener diagnóstico** | Obtener errores y advertencias para un archivo |
| **Documentación al pasar el mouse** | Obtenga información y documentación sobre el tipo en la posición |
| **Finalizaciones** | Obtenga sugerencias de finalización en la posición |

---

### Comandos de barra diagonal

| Comando | Descripción |
|---|---|
| `/ código de inicio` | Inicializar LSP para el espacio de trabajo actual |
| `/ código de inicio -f` | Forzar reinicializar LSP |
| `/estado del código` | Mostrar el estado actual de la conexión LSP |
| `/ registros de código` | Ver registros de diagnóstico de LSP |

---

*📂 Capítulo: **Hooks***

## Hooks — Kiro CLI

> **Nota:** Este archivo es un duplicado. El contenido completo de Hooks está en [07_Hooks.md](./07_Hooks.md).

---

Ver [07_Hooks.md →](./07_Hooks.md)

---

*📂 Capítulo: **Auto complete***

## Autocompletar - Kiro CLI

> **Nota:** Este archivo es un duplicado. El contenido completo de Autocompletar está en [09_Autocomplete.md](./09_Autocomplete.md).

---

Ver [09_Autocomplete.md →](./09_Autocomplete.md)

---

*📂 Capítulo: **Billing***

## Facturación — Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/billing/](https://kiro.dev/docs/cli/billing/)

---

Kiro CLI utiliza el mismo plan y sistema de crédito que el IDE. Consulte la [página de planes de Kiro](https://kiro.dev/docs/billing/) para conocer los precios actuales y los detalles de los niveles.

---

### Prácticas de facturación

Se aplican las siguientes reglas al suscribirse, actualizar, bajar de categoría o incurrir en excedentes:

#### Actualización desde Gratis → Pagado (primera vez)

Si estás en el **nivel Kiro Free**, nunca has actualizado antes y actualiza a Pro, Pro+ o Power a mitad de mes:
- Se te cobra una **tarifa prorrateada** por el resto del mes
- Obtienes acceso inmediato a los **límites de crédito completos** de tu nuevo plan
- Si actualiza nuevamente en el mismo mes, las tarifas se retrotraen proporcionalmente como si hubiera elegido el nivel superior desde el primer día.

#### Actualización entre niveles pagos

Si actualiza de un nivel pago a un nivel pago más alto a mitad de mes:
- Se le cobra una **tarifa retroactiva para todo el mes** según la diferencia de precio
- Kiro recalcula el uso de todo el mes con los créditos del nuevo nivel.
- Ejemplo: si usó 1010 créditos (10 por encima del límite Pro) y luego actualizó a Pro+, el cargo excedente se elimina según los límites del nuevo nivel.

#### Degradación

- Las rebajas **entran en vigor el mes siguiente** (las actualizaciones entran en vigor inmediatamente)
- Si baja a mitad de mes (por ejemplo, Pro+ → Pro el 2 de junio), se le cobrará la **tarifa completa para ese mes** (tarifa Pro+ completa para junio), luego la tarifa del nuevo nivel a partir del siguiente ciclo.

#### Excesos

- Si incurre en excedentes, se le cobrarán los cargos totales por excedentes del mes **al final del ciclo de facturación**

#### Renovación de crédito

- Para **todos los niveles**, su límite de uso se renueva al comienzo del **siguiente ciclo de facturación**

---

### Próximos pasos

- [Administrar su suscripción a Kiro CLI →](https://kiro.dev/docs/cli/billing/subscription-portal/)
- [Planes y facturación (IDE) →](https://kiro.dev/docs/billing/)

---

*📂 Capítulo: **Code Intelligence***

## Inteligencia de código: Kiro CLI

> **Nota:** Este archivo es un duplicado. El contenido completo de Code Intelligence está en [10_Code Intelligence.md](./10_Code%20intelligence.md).

---

Ver [10_Code Intelligence.md →](./10_Code%20intelligence.md)

---

*📂 Capítulo: **Billing for individuals > Managing your Kiro CLI subscription***

## Administrar su suscripción Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/billing/subscription-portal/](https://kiro.dev/docs/cli/billing/subscription-portal/)

---

### Accediendo al Portal de Suscripción

Accedé al portal en: **[app.kiro.dev/account/usage](https://app.kiro.dev/account/usage)**

Desde el CLI, use el comando `/usage` para ver el enlace al portal.

```
> /usage
```

---

### Qué puedes hacer en el portal

Una vez en el portal podés:

| Acción | Descripción |
|---|---|
| 📊 **Ver uso** | Ver plan actual y estadísticas de uso |
| ⬆️ **Actualizar / Degradar** | Cambiar tu suscripción |
| 💳 **Métodos de pago** | Actualizar métodos de pago e información de facturación |
| 🧾 **Facturas** | Descargar facturas e historial de facturación |
| 👥 **Administrar miembros** | Gestionar miembros del equipo (planes de equipo) |
| ❌ **Cancelar** | Cancelar tu suscripción si es necesario |

---

### Prácticas de facturación

#### Actualización desde el nivel gratuito (primera vez)

Si nunca antes actualizaste y actualizaste a mitad de mes:
- Se cobra una tarifa **prorrateada** por los días restantes
- Pero obtenés **acceso inmediato** al límite completo del nuevo plan

**Ejemplo:** Subscripción a Pro el 15 de abril → se cobra la mitad del fee mensual y se accede a todos los créditos del tier.

#### Actualizando entre aviones pagos

Si ya estás en un plan pago y subís a otro:
- Se cobra la diferencia de forma **retroactiva** para todo el mes
- Kiro recalcula el uso del mes bajo los límites del nuevo plan
- Esto puede evitar cargos de exceso si ya supera el límite anterior

#### Degradación

- Los downgrades tienen efecto al **inicio del siguiente mes**
- Las actualizaciones son **efectivas inmediatamente**
- Si baja de Pro+ a Pro a mitad de mes, pagás el fee completo de Pro+ ese mes

#### Excesos

- Si supera el límite, las solicitudes se pausan hasta que el límite se renueve al inicio del mes siguiente
- El nivel gratuito tiene límites fijos y **no permite exceso**
- En planos pagos podés habilitar overage para continuar trabajando sin interrupciones

---

### ¿Necesitas ayuda?

- Portal de soporte: [app.kiro.dev/account/usage?support_form](https://app.kiro.dev/account/usage?support_form)
- Correo electrónico: [billing@kiro.dev](mailto:billing@kiro.dev)
- Chat de ayuda en el portal de suscripción

---

*📂 Capítulo: **Billing for individuals > Managing your taxes***

## Administrar sus impuestos

> **Fuente:** [kiro.dev/docs/cli/billing/managing-taxes/](https://kiro.dev/docs/cli/billing/managing-taxes/)

---

### ¿Por qué veo Amazon Web Services, Inc. en mi compra de Kiro?

Amazon Web Services, Inc. (AWSI) es el proveedor de servicios de Kiro. AWSI:
- Está establecido y opera en Estados Unidos
- Está registrado para Impuesto sobre las Ventas en los estados correspondientes
- Está registrado para IVA en países donde las leyes de impuestos indirectos requieren que proveedores extranjeros de Servicios Suministrados Electrónicamente (ESS) se registren y cobren IVA local.

AWSI trata a Kiro como:
- **Software descargado** en EE. UU.
- **ESS (Servicios suministrados electrónicamente)** fuera de EE.UU.

---

### ¿Cómo determina AWS mi ubicación para los impuestos?

AWS usará la **dirección de facturación del cliente** provista al comprar Kiro. Si la dirección es inválida, recibirá un error `customer_tax_location_invalid`.

---

### Clientes B2B e IVA (cargo revertido)

Si sos cliente B2B y ya tenés un TRN (Número de Registro Fiscal) en tu cuenta AWS, **igualmente necesitás agregarlo a tu cuenta Kiro** a través del portal de clientes de forma separada.

En ciertas jurisdicciones, AWS debe cobrar y recolectar impuestos tanto en compras B2B como B2C.

---

### Actualización de información fiscal a mitad de mes

AWS usará tu dirección de facturación al momento de la compra, o al momento de cambios en tu suscripción (upgrades o renovaciones).

---

### Métodos de pago y monedas

| Métodos aceptados | Moneda |
|---|---|
| Todas las tarjetas de crédito principales | USD únicamente |

---

### Problemas con facturas con IVA

Si tu factura de IVA o el vendedor de AWS aparece incorrectamente, contacta al [soporte de billing de Kiro](https://app.kiro.dev/account/usage?support_form).

---

### Números de Registro Tributario (TRN)

Kiro acepta TRN según los requisitos del país del cliente. Al agregar un TRN, Kiro verificará que el formato sea correcto.

> **Nota:** El estado especial de exención de IVA (para organizaciones con status de alivio) estará disponible próximamente.

---

*📂 Capítulo: **Billing for individuals > Related questions***

## Preguntas relacionadas

> **Fuente:** [kiro.dev/docs/cli/billing/ related-questions/](https://kiro.dev/docs/cli/billing/ related-questions/)

---

### ¿Qué países/regiones soportan pagos de aviones?

Kiro soporta facturación en la mayoría de países del mundo incluyendo: Argentina, Brasil, Chile, Colombia, México, España, EE.UU., Canadá, Reino Unido, Alemania, Francia, Australia, Japón, India, y muchos más. Consulte la lista completa en [kiro.dev/docs/cli/billing/ related-questions/](https://kiro.dev/docs/cli/billing/ related-questions/).

---

### ¿Qué es un crédito?

Un **crédito** es una unidad de trabajo en respuesta a las indicaciones del usuario:
- Avisos simples: pueden consumir menos de 1 crédito
- Prompts complejos (ejemplo: ejecutar una tarea spec): sustancialmente más de 1 crédito
- **Diferentes modelos consumen créditos a diferentes tasas** — Sonnet 4 cuesta 1.3x más créditos que Auto
- Los créditos se miden hasta el segundo decimal (mínimo: 0.01 créditos)

---

### ¿Qué plan pago elegir si no estoy seguro del uso futuro?

Recomendación: **empezar con Pro** y habilitar overage si es necesario. En el primer mes pago, si subís de plan, se aplica un descuento retroactivo desde el día que empezaste a pagar, sin penalización por esperar.

---

### ¿Qué plan elegir cuando mi uso ya es estable?

Elegí el **plan más pequeño que abraza un mes típico** con algo de margen:
- Sin overage: el uso se pausa al alcanzar el límite (factura predecible)
- Con overage habilitado: continuás trabajando sin interrupciones en picos ocasionales
- Si los picos son frecuentes o el costo de excedente se acerca a la diferencia al siguiente nivel, subir de plan suele ser más económico

---

### ¿Qué pasa cuando alcanzo el límite mensual de mi plan?

- **Nivel gratuito**: las solicitudes se pausan hasta el inicio del próximo mes. No hay exceso de heno; Podés actualizar para más capacidad inmediata.
- **Planes pagos**: podrás habilitar el excedente para continuar trabajando sin interrupciones, o actualizar a un plan superior.

---

### ¿Cómo funciona la prorratización en el primer update?

En el primer mes que升级 a un plan pago, los cargos se prorratean por los días restantes en el mes:
- Ejemplo: en un mes de 30 días, si actualiza a Pro ($20) con 10 días restantes → paga $6.67 (10/30 de $20) pero obtendrás acceso completo a los límites del plan inmediatamente.
- Si en ese mismo mes subís a Pro+ ($40), se descuenta lo ya pagado y se cobra la diferencia.

---

### ¿Cómo funciona la prorratización en actualizaciones posteriores?

La prorratización **solo aplica al primer update**. Después, cualquier actualización en cualquier día del mes se cobra completo y el usuario recibe los límites completos del plan.

---

### ¿Cuándo factura Kiro?

Kiro factura en **mes calendario** (UTC). El cargo mensual exacto depende de tu zona horaria. Si actualizas a la mitad de mes, se cobra inmediatamente el costo del nuevo plan descontado el del anterior. El excedente aparece como líneas separadas en la factura del mes.

---

### ¿Por qué una sola acción puede costar más de 1 crédito?

Algunas acciones requieren mucho más contexto o generar más resultados (ej. trabajar en un código base grande o una construcción muy compleja). Cuando el uso total de tokens supera el límite de una sola solicitud, Kiro lo cuenta como más de 1 crédito.

---

### ¿Cómo optimizar Kiro mis costos?

Kiro está diseñado para minimizar el trabajo redundante de LLM:
- Reutilizar contexto donde sea posible
- Aplicación eficiencias a nivel de proveedor (uso eficiente de herramientas con token, almacenamiento en caché rápido)
- **Pagás por request, no por token**
- Los beneficios de eficiencia se reflejan en el diseño de precios, no en la gestión manual de avisos.

---

*📂 Capítulo: **Billing for individuals > Contacting billing support***

## Cómo ponerse en contacto con el soporte de facturación

> **Fuente:** [kiro.dev/docs/cli/billing/contact-support/](https://kiro.dev/docs/cli/billing/contact-support/)

---

### Cuándo contactar al soporte de facturación

Contactá al soporte de facturación para:

| Motivo | Descripción |
|---|---|
| 💳 **Problemas de pago** | Pagos fallidos, actualización de métodos de pago, errores de facturación |
| 📋 **Preguntas sobre suscripción** | Cambios de plan, asistencia con actualizaciones/bajas, ciclos de facturación |
| 🔐 **Acceso a la cuenta** | Problemas accediendo a tu cuenta o panel de facturación |
| 💰 **Solicitudes de reembolso** | Preguntas sobre reembolsos o disputas de facturación |
| 📊 **Aclaración de uso** | Entender tus cargos de uso o límites de nivel |
| 🧾 **Preguntas sobre facturas** | Solicitar copias de facturas o aclarar cargos |

---

### Cómo contactar al soporte

#### Opción 1: Línea de comando

```bash
kiro-cli issue
```

#### Opción 2: desde dentro del chat

Desde una sesión de chat activa en Kiro CLI, describe el problema a Kiro en lenguaje natural — te ayudará a crear un problema en GitHub con contexto precompletado.

Ambos métodos rutean el request al equipo de facturación.

---

### ¿Qué información necesitará?

Al crear la solicitud de soporte, incluye:

- **Título del problema** — Breve descripción del problema de facturación
- **Descripción detallada** — Información específica sobre tu consulta
- **Detalles de la cuenta** — Email de tu cuenta Kiro y datos de suscripción
- **Context** — Mensajes de error relevantes o circunstancias del problema

---

### Consejos para solicitudes de soporte eficaces

- **Sé específico** — Describí claramente el problema de facturación
- **Incluí detalles relevantes** — Email de cuenta, nivel de suscripción, fechas aproximadas
- **Mencioná intentos previos** — Si ya intentaste algún problema, indícalo

> Para preguntas generales del producto o soporte técnico: [documentación](https://kiro.dev/docs) | [Discordia](https://discord.gg/kirodotdev) | [GitHub](https://github.com/kirodotdev/kiro)

---

### Recursos alternativos

Antes de contactar soporte, busca tu respuesta en:

- [Resumen de facturación →](https://kiro.dev/docs/cli/billing/)
- [Preguntas frecuentes →](https://kiro.dev/faq)
- [Solución de problemas →](https://kiro.dev/docs/troubleshooting)

---

*📂 Capítulo: **Enterprise > Concepts***

## Conceptos

> **Fuente:** [kiro.dev/docs/cli/enterprise/concepts/](https://kiro.dev/docs/cli/enterprise/concepts/)

---

Glosario de términos clave para administradores que gestionan suscripciones y usuarios de Kiro Enterprise.

---

### Centro de identidad de AWS IAM

Servicio de AWS que proporciona un lugar centralizado para gestionar las identidades de los suscriptores de Kiro.

---

### Región de AWS

Una ubicación física donde AWS agrupa sus centros de datos. Existen dos regiones relevantes para administradores de Kiro:

1. La región donde está habilitada tu instancia de IAM Identity Center (donde se gestionan identidades y se almacenan suscripciones)
2. La región donde se crea tu perfil de Kiro (donde se almacenan los datos — puede ser diferente)

Ver [regiones soportadas →](./11_regiones soportadas.md) para más información.

---

### Grupo

Una colección de usuarios dentro de IAM Identity Center. Al suscribir un grupo a Kiro, los usuarios dentro de él se suscriben **individualmente** (no existe el concepto de suscripción grupal).

---

### Consola Kiro

Una consola dentro de la Consola AWS donde los administradores crean y gestionan suscripciones de Kiro y controlan la configuración. Aparece como **"Kiro"** en el menú desplegable de servicios de AWS.

---

### Créditos Kiro

Unidad de consumo que mide el uso de las funcionalidades de AI de Kiro. Los créditos se gastan al interactuar con capacidades de AI y se reabastecen según el nivel de suscripción.

---

### Usuario empresarial de Kiro

Un que fue agregado y suscrito a un nivel de suscripción de usuario de Kiro a través de la Consola AWS. Puede acceder a Kiro mediante IAM Identity Center, Okta o Microsoft Entra ID.

---

### Perfil de Kiro

La abstracción de gestión que define y aplicaciones administrativas y suscripciones a usuarios empresariales en una cuenta y región de AWS específicas.

Características:
- Corresponde a una combinación de cuenta AWS (administración o miembro) + región
- Solo puede existir **un perfil por cuenta AWS en una región dada**
- Se configura a través de la Consola Kiro

---

### Nivel de suscripción de Kiro

Un plan de precios específico con un número predeterminado de créditos Kiro.

---

### Tabla resumen

| Concepto | Descripción breve |
|---|---|
| **Centro de identidad IAM** | Gestión centralizada de identidades |
| **Región de AWS** | Ubicación física de los centros de datos |
| **Grupo** | Colección de usuarios (suscripción individual) |
| **Consola Kiro** | UI en AWS Console para gestionar Kiro |
| **Créditos Kiro** | Unidad de consumo de IA |
| **Usuario empresarial** | Usuario suscrito vía Consola AWS |
| **Perfil de Kiro** | Abstracción de gestión por cuenta + región |
| **Nivel de suscripción** | Plan de precios con créditos predeterminados |

---

*📂 Capítulo: **Enterprise > Onboarding quickstart***

## Inicio rápido de incorporación

> **Fuente:** [kiro.dev/docs/cli/enterprise/getting-started/](https://kiro.dev/docs/cli/enterprise/getting-started/)

---

### Audiencia

Esta guía está dirigida a **administradores** que desean incorporar su equipo a Kiro y gestionar sus suscripciones.

---

### Para incorporar tu equipo a Kiro

#### Paso 1 — Crear una cuenta AWS

Si no tienes una, [creá una cuenta AWS](https://docs.aws.amazon.com/accounts/latest/reference/manage-acct-creating.html).

#### Paso 2 — Iniciar sesión en AWS

Podés iniciar como:
- Usuario raíz de AWS
- Usuario con un rol privilegiado
- O [configurar permisos mínimos para administradores](https://kiro.dev/docs/cli/enterprise/iam/#policy-allow-administrators-to-configure-kiro-and-subscribe-users)

#### Paso 3 — Conectar tu proveedor de identidad

Conectar a tu proveedor de identidad. Podés:
- Agregar usuarios directamente desde **AWS IAM Identity Center**
- Conectar a un IdP externo: **Okta** o **Microsoft Entra ID**

Ver [Conectando tu proveedor de identidad →](./03_Conectando tu proveedor de identidad.md) para instrucciones detalladas.

#### Paso 4 — Crear un perfil de Kiro y suscribir usuarios

Dentro de la consola de AWS:
1. Navegar a la **Consola Kiro**
2. Usar la UI disponible para crear un perfil
3. El perfil conecta las identidades de usuario con sus suscripciones y configuraciones de Kiro
4. Una vez creado, importa usuarios y grupos
5. [Suscribir el equipo a Kiro](https://kiro.dev/docs/cli/enterprise/subscribe)

> Solo puede existir **un perfil por cuenta AWS en una región dada**.

#### Paso 5 — Los usuarios verifican su correo electrónico

Dentro de las **24 horas** de ser suscritos, los usuarios recibirán un correo electrónico con:
- Instrucciones de descarga para Kiro IDE y Kiro CLI
- Instrucciones de inicio de sesión

Alternativamente, pueden descargar Kiro desde [kiro.dev](https://kiro.dev/).

---

### Referencia rápida

```
Admin → AWS Console → Kiro Console → Crear Profile 
      → Importar usuarios/grupos → Suscribir al plan
      
Usuario ← Email con instrucciones ← Kiro backend
```

---

*📂 Capítulo: **Enterprise > Connecting your identity provider***

## Conectando su proveedor de identidad

> **Fuente:** [kiro.dev/docs/cli/enterprise/identity-provider/](https://kiro.dev/docs/cli/enterprise/identity-provider/)

---

Kiro admite conectarse a su proveedor de identidad externo directamente o a través de AWS IAM Identity Center.

---

### Fuentes de identidad admitidas

| Fuente de identidad | Tipo |
|---|---|
| **Centro de identidad de AWS IAM** | Nativo de AWS |
| **Okta** | IdP externo directo |
| **ID de Microsoft Entra** | IdP externo directo |

---

### Opción 1: Centro de identidad de AWS IAM

Seguí las instrucciones en la [guía de IAM Identity Center →](https://kiro.dev/docs/cli/enterprise/identity-provider/iam-identity-center)

Pasos generales:
1. Habilitar IAM Identity Center en tu cuenta AWS
2. Agregar usuarios a tu directorio
3. Conectar IAM Identity Center a Kiro desde la Kiro Console

---

### Opción 2: Proveedor de identidad externo (directo)

#### Okta

Seguí la [guía de configuración de Okta →](https://kiro.dev/docs/enterprise/identity-provider/okta)

Pasos generales:
1. Crea una aplicación Kiro en tu inquilino de Okta
2. Configurar SAML/SCIM según las instrucciones
3. Conectar desde la consola Kiro

#### ID de Microsoft Entra (Azure AD)

Seguí la [guía de configuración de Microsoft Entra →](https://kiro.dev/docs/enterprise/identity-provider/microsoft-entra)

Pasos generales:
1. Registrador Kiro como Enterprise Application en Entra ID
2. Configurar SSO y aprovisionamiento
3. Conectar desde la consola Kiro

---

### Siguiente paso

Una vez conectado el proveedor de identidad, podrás suscribir a esos usuarios o grupos a Kiro como se describe en la [guía de suscripción →](./04_Subscribe your team.md).

---

*📂 Capítulo: **Enterprise > Subscribe your team***

## Suscríbete a tu equipo

> **Fuente:** [kiro.dev/docs/cli/enterprise/subscribe/](https://kiro.dev/docs/cli/enterprise/subscribe/)

---

Una vez que tu proveedor de identidad esté conectado y tu perfil de Kiro esté creado, podrás suscribir usuarios o grupos a Kiro desde la Kiro Console.

---

### Usuarios suscritos

1. Iniciar sesión en **AWS Management Console**
2. Navegar a la **Kiro Console** (si no la ves, verifica que estás en la región AWS correcta)
3. Vaya a **Usuarios y grupos → pestaña Usuarios**
4. Seleccionar el usuario a suscribir
5. Elegir el plan de suscripción
6. Confirmar

### Grupos de suscripción

1. Repetir los pasos 1-3 anteriores
2. Ir al **Pestaña Grupos**
3. Seleccionar el grupo
4. Elegir el plan de suscripción y confirmar

> Al suscribir un grupo, **cada usuario dentro del grupo** se suscribe individualmente. No existe suscripción grupal como unidad de cobro.

---

### Después de suscribirse

Dentro de las **24 horas**, los usuarios suscritos recibirán un correo electrónico con:
- Instrucciones de descarga para Kiro IDE y Kiro CLI
- Instrucciones de inicio de sesión con su proveedor de identidad

---

### Estados de suscripción

| Estado | Descripción |
|---|---|
| **Activo** | El usuario está suscrito a Kiro. Se le cobra. |
| **Cancelado** | La suscripción fue cancelada por un administrador. Sin acceso a características pagas. |
| **Pendiente** | Suscrito pero no ha activado aún su suscripción. No se cobra. |

Los estados se visualizan en la página **Suscripciones** de la Kiro Console (solo en la pestaña Usuarios, no en Grupos).

---

*📂 Capítulo: **Enterprise > Manage subscriptions***

## Administrar suscripciones

> **Fuente:** [kiro.dev/docs/cli/enterprise/subscription-management/](https://kiro.dev/docs/cli/enterprise/subscription-management/)

---

### Cambiar los planes de suscripción de Kiro

1. Iniciar sesión en **AWS Management Console**
2. Navegar a la **Kiro Console** (si no la ves, verificará la región de AWS)
3. Vaya a **Usuarios y Grupos → pestaña Usuarios o Grupos**
4. Seleccionar el usuario o grupo
5. Elegir **Cambiar plan** → seleccionar el nuevo plan → **Continuar**

**Tiempo:**
- **Upgrade** (plan mayor): cambios **inmediatos**
- **Downgrade** (plan menor): cambios al **inicio del próximo mes**

Ver [Facturación empresarial →](./09_Billing.md) para detalles sobre qué incluye cada nivel.

---

### Darse de baja de usuarios de Kiro

1. Iniciar sesión en **AWS Management Console**
2. Navegar a la **Consola Kiro**
3. Vaya a **Usuarios y Grupos → pestaña Usuarios o Grupos**
4. Seleccionar el usuario o grupo a cancelar
5. Elegir **Desactivar plan** → revisar el diálogo → **Cancelar suscripción**

> Después de cancelar, la suscripción se marca como **Cancelada**. El pierde acceso **inmediatamente** a las características pagas de los usuarios.

---

### Eliminación automática de suscripción

Las suscripciones pueden eliminarse automáticamente cuando:
- Un usuario es eliminado del proveedor de identidad.
- Un usuario es eliminado del grupo suscrito

---

### Habilitar excedentes para usuarios de Kiro

El excedente permite a los usuarios continuar trabajando cuando superan los límites de su plan.

**Ventajas:**
- ✅ **Productividad ininterrumpida** durante picos de uso
- ✅ **Mejor comprensión del uso real** para dimensionar futuras suscripciones

**Por defecto, el exceso está deshabilitado.** Una vez habilitado, aplica a **todos los usuarios y grupos del perfil**.

Para habilitar:
1. Iniciar sesión en **AWS Management Console**
2. Navegar a la **Consola Kiro**
3. Vaya a **Configuración**
4. En la sección **Configuración de Kiro**, activa **Excedentes**

> Los tapones personalizados de excedente no están disponibles aún (próximamente).

---

### Estados de suscripción

| Estado | Descripción | ¿Se cobra? |
|---|---|---|
| **Activo** | Suscrito y activo | ✅Sí |
| **Cancelado** | Cancelado por admin | ❌ No |
| **Pendiente** | Suscrito sin activar | ❌ No |

---

*📂 Capítulo: **Enterprise > Governance***

## Gobernanza

> **Fuente:** [kiro.dev/docs/cli/enterprise/governance/](https://kiro.dev/docs/cli/enterprise/governance/)

---

Como administrador, podrás controlar qué **modelos** y **servidores MCP** están disponibles para tus usuarios. Estos controles de gobernanza se gestionan desde la **Kiro Console → Configuración → Configuración compartida**.

---

### Gobernanza modelo

Por defecto, los usuarios pueden acceder a **cualquier modelo soportado por Kiro**. Podés restringir esto:

| Acción | Descripción |
|---|---|
| **Activar gestión de acceso al modelo** | Habilitar la gestión de acceso a modelos |
| **Seleccionar lista aprobada** | Elegir qué modelos pueden usar los usuarios |
| **Definir modelo por defecto** | Establecer un modelo que se aplica automáticamente a todos los clientes |

Para más detalles, ver [Modelos →](https://kiro.dev/docs/cli/enterprise/governance/model)

---

### Gobernanza del MCP

Por defecto, los usuarios pueden usar **cualquier servidor MCP** en su cliente Kiro. Podés:

| Opción | Descripción |
|---|---|
| **Deshabilitar MCP completamente** | Los usuarios no pueden usar ningún servidor MCP |
| **Lista de servidores permitidos** | Especificar una lista de servidores MCP aprobados mediante un registro MCP |

Estas políticas pueden establecerse a nivel de **organización** o sobreescribirse por **cuenta individual**.

Para más detalles, ver [Herramientas MCP →](https://kiro.dev/docs/cli/enterprise/governance/mcp)

---

### Cómo configurar

1. Abrir la **Consola Kiro** en AWS
2. Vaya a **Configuración → Configuración compartida**
3. Configurar las opciones de Model Governance o MCP Governance

---

### Controles empresariales adicionales

Desde **Configuración** también podés controlar:

| Configuración | Descripción |
|---|---|
| **Cifrado en reposo** | Cifrado de datos almacenados |
| **Referencias de código** | Control de referencias de código |
| **Seguimiento de uso** | Panel de uso de la organización |
| **Registro rápido** | Registro de avisos de usuarios |
| **Herramientas web** | Habilitar/deshabilitar `web_search` y `web_fetch` para todos los usuarios |
| **Excedentes** | Habilitar excedentes para usuarios del perfil |

---

*📂 Capítulo: **Enterprise > Monitor and track***

## Monitorear y rastrear

> **Fuente:** [kiro.dev/docs/cli/enterprise/](https://kiro.dev/docs/cli/enterprise/) | [kiro.dev/docs/cli/enterprise/settings/](https://kiro.dev/docs/cli/enterprise/settings/)

---

Kiro Enterprise proporciona herramientas para que los administradores monitoreen y rastreen el uso de la plataforma.

---

### Panel de uso

Visualice el uso de Kiro a nivel de organización desde la **Kiro Console**:

- Créditos consumidos por período
- Usuarios activos
- Distribución de uso por nivel

**Cómo acceder:**
1. Iniciar sesión en la **AWS Management Console**
2. Navegar a la **Consola Kiro**
3. Ver la sección de **Uso/Panel**

---

### Actividad por usuario

Visualice la actividad individual de los usuarios:
- Última actividad por usuario (columna `Última activa` en la página de Suscripciones)
- Usuarios con estado **Pending** no tendrán datos en esta columna (no han activado su suscripción)

---

### Registro rápido

Los administradores pueden habilitar el registro de mensajes de los usuarios para auditoría y cumplimiento.

**Para habilitar:**
1. Abrir la **Consola Kiro**
2. Vaya a **Configuración**
3. Activar **Registro rápido**

Ver [Registrar mensajes de usuario →](https://kiro.dev/docs/cli/enterprise/monitor-and-track/prompt-logging)

---

### Control de herramientas web

Los administradores pueden deshabilitar las herramientas web (`web_search` y `web_fetch`) para todos los usuarios:

1. Abrir la **Consola Kiro**
2. Vaya a **Configuración → Configuración compartida**
3. Desactivar **Herramientas de búsqueda y recuperación web**

Cuando están deshabilitados, los usuarios ven una notificación en `/tools` indicando que el administrador deshabilitó el acceso web.

---

### Controles de monitoreo disponibles

| Controlar | Descripción |
|---|---|
| **Panel de uso** | Uso agregado de la organización |
| **Actividad por usuario** | actividad individual |
| **Registro rápido** | Auditoría de avisos |
| **Estados de suscripción** | Activo / Cancelado / Pendiente por usuario |

---

*📂 Capítulo: **Enterprise > Settings***

## Ajustes

> **Fuente:** [kiro.dev/docs/cli/enterprise/settings/](https://kiro.dev/docs/cli/enterprise/settings/)

---

Un administrador puede controlar las siguientes configuraciones dentro de un **perfil de Kiro**.

---

### Configuraciones disponibles

| Configuración | Descripción |
|---|---|
| **Cifrado en reposo** | Cifrado de datos en reposo para el perfil |
| **Panel de uso** | Visualizar el uso de Kiro a nivel de organización |
| **Actividad por usuario** | Ver la actividad individual de cada usuario |
| **Registro rápido** | Registrar los avisos de los usuarios para auditoría |
| **Herramientas web** | Habilitar/deshabilitar `web_search` y `web_fetch` |
| **Organizaciones de AWS** | Integración con AWS Organizations |
| **Excedentes** | Habilitar overages para todos los usuarios del perfil |
| **Gobernanza modelo** | Controlar qué modelos pueden usar los usuarios |
| **Gobernanza del MCP** | Controlar qué servidores MCP pueden usar los usuarios |

---

### Cómo acceder a la configuración

1. Iniciar sesión en la **AWS Management Console**
2. Navegar a la **Consola Kiro**
3. Vaya a **Configuración**
4. Configurar las opciones disponibles

---

### Configuración de herramientas web

La configuración **Herramientas web** controla si los usuarios pueden usar `web_search` y `web_fetch` para buscar en la web y obtener contenido de URL.

**Para deshabilitar herramientas web:**
1. Abrir la **Consola Kiro**
2. Vaya a **Configuración → Configuración compartida**
3. Desactivar **Herramientas de búsqueda y recuperación web**

Cuando están deshabilitados, los usuarios ven una notificación en `/tools` indicando que el administrador deshabilitó el acceso web.

---

### Alcance de la configuración

Los ajustes pueden configurarse a diferentes niveles:

| Nivel | Descripción |
|---|---|
| **Nivel de organización** | Aplicación a toda la organización |
| **Nivel de cuenta** | Sobreescribe la configuración de la organización para una cuenta específica |

Ver [Governance →](./06_Governance.md) para detalles sobre los controles de modelos y MCP.

---

*📂 Capítulo: **Enterprise > Billing***

## Facturación

> **Fuente:** [kiro.dev/docs/cli/enterprise/billing/](https://kiro.dev/docs/cli/enterprise/billing/)

---

### Descripción general de facturación empresarial

La facturación Enterprise de Kiro se gestiona a través de la **AWS Console**, a diferencia de los usuarios individuales que usan el portal de Kiro directamente.

---

### Niveles de suscripción

Los administradores pueden suscribir usuarios a diferentes niveles según las necesidades del equipo. Cada nivel incluye:
- Un número predeterminado de **Kiro credits** por mes
- Acceso a diferentes funciones según el plan.

Ver [Precios →](https://kiro.dev/pricing/) para la comparación actualizada de niveles y precios.

---

### Cómo funciona la facturación empresarial

- La facturación se realiza **por usuario suscrito activo** mensualmente
- Los usuarios con estado **Pending** (no activados) **no se cobran**
- Los cambios de plan toman efecto:
  - **Actualizaciones**: inmediatamente
  - **Downgrades**: al inicio del próximo mes

---

### excedentes

Por defecto, los excedentes están **deshabilitados**. Los administradores pueden habilitarlos para permitir que los usuarios continúen trabajando para superar su límite mensual.

Para habilitar excedentes ver [Administrar suscripciones → Habilitar excedentes →](./05_Manage suscripciones.md)

---

### Ver información de facturación

Los administradores pueden ver:
- Panel de uso de la organización en la **Kiro Console**
- Actividad por usuario
- Costos de excedente (si están habilitados)

---

### Contactar con el soporte de facturación

Para consultas de facturación Empresarial:
- [Portal de soporte de facturación →](https://app.kiro.dev/account/usage?support_form)
- Correo electrónico: [billing@kiro.dev](mailto:billing@kiro.dev)

---

*📂 Capítulo: **Enterprise > IAM***

## SOY

> **Fuente:** [kiro.dev/docs/cli/enterprise/iam/](https://kiro.dev/docs/cli/enterprise/iam/)

---

### Permisos de IAM para administradores empresariales

Los administradores de Kiro Enterprise necesitan permisos específicos de IAM para gestionar la plataforma desde la consola AWS.

---

### Política: Permitir a los administradores configurar Kiro y suscribir usuarios

Para que los administradores puedan configurar Kiro y suscribir usuarios **sin permisos de root**, podés asignarles una política IAM con permisos mínimos:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "kiro:*",
        "sso:ListInstances",
        "sso:ListPermissionSets",
        "identitystore:ListUsers",
        "identitystore:ListGroups",
        "identitystore:DescribeUser",
        "identitystore:DescribeGroup"
      ],
      "Resource": "*"
    }
  ]
}
```

---

### Resumen de permisos requeridos

| permiso | Descripción |
|---|---|
| `kiro:*` | Acceso completo a la consola Kiro |
| `sso:ListInstances` | Listar instancias de IAM Identity Center |
| `sso:ListPermissionSets` | Ver conjuntos de permisos de SSO |
| `almacén de identidades:ListUsers` | Listar usuarios en el directorio |
| `almacén de identidades:ListGroups` | Listar grupos en el directorio |
| `identitystore:DescribeUser` | Ver detalles de usuarios |
| `almacén de identidad:DescribeGroup` | Ver detalles de grupos |

---

### Iniciar sesión

Podés iniciar sesión en la consola AWS como:
- **Usuario root de AWS** (no recomendado para uso cotidiano)
- **Usuario con rol privilegiado** (recomendado)
- **Usuario con permisos mínimos** según la política de arriba

---

### Relacionado

- [Inicio rápido de incorporación →](./02_Inicio rápido de incorporación.md)
- [Conectando tu proveedor de identidad →](./03_Conectando tu proveedor de identidad.md)
- [Documentos del Centro de identidad de IAM →](https://kiro.dev/docs/cli/enterprise/identity-provider/iam-identity-center)

---

*📂 Capítulo: **Enterprise > Supported regions***

## Regiones admitidas

> **Fuente:** [kiro.dev/docs/cli/enterprise/supported-regions/](https://kiro.dev/docs/cli/enterprise/supported-regions/)

---

### Descripción general

Kiro Enterprise opera en regiones específicas de AWS. Al configurar tu **Kiro Profile**, tendrás que tener en cuenta dos tipos de regiones:

1. **Región de IAM Identity Center** — Donde se gestionan las identidades de usuario y se almacenan las suscripciones
2. **Perfil Región del Kiro** — Donde se almacenan los datos de usuario (puede ser diferente)

---

### Notas importantes sobre las regiones

- Si usás **IAM Identity Center**, la región donde está habilitada tu instancia es donde se gestionan las identidades
- La región del **Kiro Profile** es donde se almacenan los datos — puede ser una región diferente a la de IAM Identity Center
- Si no ves la **Consola Kiro** en la Consola AWS, verifica que estés en la **Región AWS correcta**

---

### Seleccionar la región correcta

Al configurar Kiro Enterprise:
1. Verifique en qué región está habilitada su instancia de IAM Identity Center
2. Elegí la región del Kiro Profile según dónde querrás almacenar los datos
3. Asegurate de que la región del Kiro Profile sea consistente con tus requisitos de residencia de datos y cumplimiento

---

### Consideraciones de residencia de datos

La región donde se crea el Kiro Profile determina dónde se almacenan los datos de los usuarios. Considerá:
- **Requisitos contractuales** de residencia de datos
- **Regulaciones locales** (ej. GDPR en Europa)
- **Latencia** para los usuarios finales

---

### Relacionado

- [Concepts →](./01_Concepts.md) — Definición de región AWS en el contexto de Kiro
- [Privacidad y seguridad →](https://kiro.dev/docs/cli/privacy-and-security/)
- [Documentación de regiones de AWS →](https://docs.aws.amazon.com/general/latest/gr/rande.html)

---

*📂 Capítulo: **Troubleshooting***

## Solución de problemas: Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/troubleshooting/](https://kiro.dev/docs/cli/troubleshooting/) | [kiro.dev/docs/cli/reference/cli-commands/](https://kiro.dev/docs/cli/reference/cli-commands/)

---

### Herramientas de diagnóstico

#### Diagnóstico automático

```bash
kiro-cli doctor          # Diagnóstico estándar
kiro-cli doctor --all    # Todos los checks disponibles
kiro-cli doctor --strict # Modo estricto (falla en warnings)
```

#### Informe completo del sistema

```bash
kiro-cli diagnostic
kiro-cli diagnostic --format json-pretty   # Output estructurado
kiro-cli diagnostic --force                # Sin requerir que la app esté corriendo
```

#### Registros de depuración

```bash
kiro-cli --verbose chat "..."    # -v / -vv / -vvv para más detalle
kiro-cli diagnostic              # Ver versión, OS, env vars, paths
```

#### Volcado de registros para soporte

Desde el chat:
```
> /logdump # Registros de chat
> /logdump --mcp # Chat + registros del servidor MCP
```
Cree un archivo `q-logs-YYYY-MM-DDTHH-MM-SSZ.zip` en el directorio actual.

---

### Problemas de autenticación

#### Error "Ya he iniciado sesión"

```bash
kiro-cli logout
kiro-cli login
```

#### El navegador no se abre (SSH/Remoto)

```golpecito
inicio de sesión de kiro-cli --use-device-flow
```
Muestra un código de dispositivo y URL para autenticar desde otro dispositivo.

#### La autenticación del Centro de identidad falla

Verifica con tu administrador:
- URL correcta del Centro de Identidad
- Región AWS correcta
- Permisos IAM asignados

```bash
kiro-cli login --license pro \
  --identity-provider https://my-org.awsapps.com/start \
  --region us-east-1
```

#### Ver usuario actual

```bash
kiro-cli whoami
kiro-cli whoami --format json-pretty
```

---

### Problemas de instalación

#### Comando `kiro-cli` no encontrado

```golpecito
cual kiro-cli
## Verificar que la ruta esté en $PATH

## Agregar al .zshrc / .bashrc:
exportar RUTA="$HOME/.local/bin:$RUTA"
```

#### Actualizar a la última versión

```bash
kiro-cli update
kiro-cli update --non-interactive
```

#### Reinstalar integraciones

```bash
kiro-cli integrations reinstall
kiro-cli integrations status
```

---

### Problemas de chat/conectividad

#### Red/Proxy

```golpecito
exportar HTTPS_PROXY=http://proxy.company.com:8080
exportar NO_PROXY=localhost,127.0.0.1

## Verificar conectividad
rizo -v https://api.kiro.dev/health
```

#### Tiempo de espera de API

```bash
kiro-cli settings api.timeout 60    # Aumentar a 60s (default: 30s)
```

#### Ventana contextual llena

Kiro compacta automáticamente el contexto. Para hacerlo manualmente:
```
> /compacto
```

---

### Problemas con el servidor MCP

#### Servidor MCP no iniciado

```golpecito
## Ver estado de servidores MCP
lista de mcp de kiro-cli
estado de kiro-cli mcp --nombre mi-servidor

## Verificar en el chat
> /mcp

## Forzar fallo si MCP es crítico
chat de kiro-cli --require-mcp-startup ...
```

#### Registros de servidores MCP

```
> /logdump --mcp
```

#### Tiempo de espera de inicialización

```bash
kiro-cli settings mcp.initTimeout 30    # Aumentar timeout (default: 10s)
```

---

### Problemas con el agente personalizado

#### Agente no se carga

```bash
kiro-cli agent list             # Verificar que aparece en la lista
kiro-cli agent validate         # Validar configuración JSON
kiro-cli agent edit my-agent    # Editar y corregir
```

#### Errores de JSON en configuración

```bash
## Validar JSON manualmente
cat ~/.kiro/agents/my-agent.json | python3 -m json.tool
```

Ver [Solución de problemas de agentes personalizados →](./04_Custom%20agents/04_Troubleshooting.md) para errores específicos.

---

### Problemas de inteligencia de código

#### LSP no responde

```bash
> /code init -f    # Forzar reinicialización
> /code status     # Ver estado del servidor LSP
> /code logs       # Ver logs de LSP
```

---

### Problemas de autocompletar

#### Autocompletado no funciona

```bash
kiro-cli doctor    # Verificar instalación
## Reiniciar terminal después de instalación
## Verificar integración en .bashrc / .zshrc
```

#### Sugerencias en línea deshabilitadas

```bash
kiro-cli inline enable
kiro-cli inline status
```

---

### Problemas de notificación

#### Crear un problema de soporte

```bash
kiro-cli issue
kiro-cli issue "Brief description of the problem"
```

Desde el chat:
```
> /problema
```

#### Información útil para soporte

Al reportar un problema, incluya:
- Salida de `kiro-cli diagnostic`
- Versión: `versión kiro-cli`
- Sistema operativo y shell
- Pasos para reproducir el problema
- Registros relevantes (`/logdump`)

---

### Códigos de salida comunes

| Código | causa |
|---|---|
| `0` | Éxito |
| `1` | Errores generales |
| `2` | Argumentos inválidos |
| `3` | Servidor(es) MCP no iniciaron |

Ver [Códigos de salida →](./17_Reference/04_Exit%20codes.md) para más detalles.

---

*📂 Capítulo: **Privacy and security > Data protection***

## Protección de datos

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/data-protection/](https://kiro.dev/docs/cli/privacy-and-security/data-protection/)

---

### Almacenamiento de datos

Kiro almacena tus preguntas, sus respuestas y contexto adicional (como código) para generar nuevas respuestas a tus solicitudes.

---

### Cifrado de datos

#### Cifrado en tránsito

Toda la comunicación entre el cliente Kiro CLI y los servicios de AWS está cifrada usando **TLS (Transport Layer Security)**.

#### Cifrado en reposo

Los datos almacenados en la infraestructura de AWS están cifrados en reposo. Los administradores Enterprise pueden configurar opciones adicionales de cifrado desde la Kiro Console.

---

### Procesamiento entre regiones

#### Inferencia entre regiones

Para mejorar la disponibilidad y el rendimiento, Kiro puede procesar solicitudes usando infraestructura en múltiples regiones AWS.

#### Regiones admitidas

Kiro ofrece inferencia entre regiones en regiones de AWS seleccionadas. Para características experimentales se puede utilizar **inferencia global entre regiones**.

---

### Mejora del servicio

Para ayudar a Kiro a proporcionar información más relevante, AWS puede usar cierto contenido de Kiro — como preguntas que hace, otros inputs, y las respuestas y código que genera — para **mejora del servicio**.

#### Contenido utilizado para mejorar el servicio

El contenido puede incluir:
- Indicaciones y preguntas
- Insumos adicionales
- Respuestas generadas
- Código producido

---

### Optar por no compartir datos

Por defecto, Kiro recopila datos de uso, errores, crash reports y otras métricas de usuarios del **Free Tier** y **suscriptores individuales**.

> Los **usuarios Enterprise** son automáticamente excluidos de la recolección de telemetría y contenido por AWS. La configuración de telemetría para Enterprise es controlada por el administrador desde la Kiro Console.

#### Optar por no participar en la CLI

```bash
kiro-cli settings telemetry.enabled false
```

#### Optar por no participar en el IDE

Vaya a **Configuración → Privacidad** y desmarcar las opciones de uso de datos.

---

### Tipos de telemetría recopilados

| Tipo | Descripción |
|---|---|
| Datos de uso | Comandos usados, frecuencia de uso |
| Errores | Errores y excepciones |
| Informes de fallos | Informe de fallos de la aplicación |
| Métricas | Métricas de rendimiento y latencia |
| Contenido (suscripción voluntaria) | Avisos y respuestas para mejorar el servicio |

---

*📂 Capítulo: **Privacy and security > Compliance validation***

## Validación de cumplimiento

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/compliance/](https://kiro.dev/docs/cli/privacy-and-security/compliance/)

---

### Descripción general

AWS, como proveedor de Kiro, mantiene una amplia gama de certificaciones de cumplimiento y programas de seguridad. La responsabilidad compartida entre AWS y el cliente aplica al uso de Kiro.

---

### Programas de cumplimiento de AWS

Kiro está construido sobre la infraestructura de AWS, la cual cuenta con certificaciones de seguridad y cumplimiento reconocidas globalmente:

| Programa | Descripción |
|---|---|
| **SOC 1, 2, 3** | Informes de Control de Organización de Servicios |
| **ISO 27001** | Gestión de Seguridad de la Información |
| **ISO 27017** | Controles de seguridad en la nube |
| **ISO 27018** | Protección de Datos Personales en la Nube |
| **PCI DSS** | Estándar de seguridad de datos de la industria de tarjetas de pago |
| **FedRAMP** | Programa Federal de Gestión de Riesgos y Autorizaciones (Gobierno de EE. UU.) |
| **RGPD** | Reglamento General de Protección de Datos (UE) |
| **HIPAA** | Ley de Responsabilidad y Portabilidad del Seguro Médico |

---

### Modelo de responsabilidad compartida

AWS opera bajo el **Modelo de Responsabilidad Compartida**:

| Responsabilidad de AWS | Responsabilidad del Cliente |
|---|---|
| Seguridad física de centros de datos | Gestión de credenciales y accesos |
| Infraestructura de red | Configuración de permisos IAM |
| Hipervisor y hardware | Datos que se envían a Kiro |
| Cifrado en tránsito y en reposo | Cumplimiento de las regulaciones locales |

---

### Cumplimiento empresarial

Los usuarios de Enterprise tienen controles adicionales:
- **Exclusión automática de telemetría** — Datos no usados para mejora del servicio
- **Registro rápido** — Para auditoría interna
- **Cifrado en reposo configurable** — Control adicional sobre cifrado de datos
- **Selección de región** — Control sobre dónde se almacenan los datos

---

### Residencia de datos

La región donde se crea el Kiro Profile determina dónde se almacenan los datos. Ver [regiones soportadas →](../14_Enterprise/11_supportedregions.md) para más detalles.

---

### Recursos adicionales

- [Programas de cumplimiento de AWS →](https://aws.amazon.com/compliance/programs/)
- [Aviso de privacidad de AWS →](https://aws.amazon.com/privacy/)
- [Política de privacidad de Kiro →](https://aws.amazon.com/privacy/)
- [Política de IA responsable de AWS →](https://aws.amazon.com/ai/responsible-ai/policy/)

---

*📂 Capítulo: **Privacy and security > Infrastructure security***

## Seguridad de infraestructura

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/infrastructure-security/](https://kiro.dev/docs/cli/privacy-and-security/infrastructure-security/)

---

### Descripción general

Kiro está construido sobre la infraestructura global de AWS, diseñado con múltiples capas de controles de seguridad física, de red y operativas.

---

### Seguridad física

AWS mantiene seguridad física de nivel militar en sus centros de datos:
- Acceso biométrico y de múltiples factores
- Personal de seguridad 24/7
- CCTV y sistemas de detección de intrusiones.
- Destrucción segura de medios físicos

---

### Seguridad de la red

| Medida | Descripción |
|---|---|
| **Protección DDoS** | AWS Shield Standard incluido (Shield Advanced disponible) |
| **Aislamiento de red** | VPC con subredes privadas |
| **Filtrado de tráfico** | Grupos de Seguridad y ACL de Red |
| **Cifrado TLS** | Todo el tráfico cifrado en tránsito |
| **Puntos finales de VPC** | Comunicación privada sin salir a Internet público |

---

### Seguridad operativa

- Monitoreo continuo de amenazas con **AWS GuardDuty**
- Registro centralizado con **AWS CloudTrail**
- Escaneo de vulnerabilidades regular
- Equipo de seguridad dedicado (AWS Security)
- Programa de divulgación responsable de vulnerabilidades

---

### Comunicación de red Kiro CLI

El CLI Kiro se comunica únicamente con los endpoints de AWS:

```
api.kiro.dev         → API principal de Kiro
auth.kiro.dev        → Autenticación
```

Toda la comunicación usa **HTTPS/TLS 1.2+**.

---

### Consideraciones sobre firewall y proxy

Si tu organización utiliza firewalls o proxies, necesitarás permitir el tráfico a los endpoints de Kiro. Ver [Firewalls, proxies y perímetros de datos →](./05_Firewalls, proxies y perímetros de datos.md) para configuración detallada.

---

### Respuesta a incidentes

AWS mantiene planes documentados de respuesta a incidentes de seguridad. En caso de un incidente de seguridad relacionado con Kiro:
1. Reportar a [soporte de facturación de Kiro](https://app.kiro.dev/account/usage?support_form)
2. Revisar [Boletines de seguridad de AWS](https://aws.amazon.com/security/security-bulletins/)
3. Seguir los procedimientos internos de respuesta a incidentes de tu organización.

---

*📂 Capítulo: **Privacy and security > IAM permissions***

## Permisos de IAM

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/iam/](https://kiro.dev/docs/cli/privacy-and-security/iam/)

---

### Descripción general

Kiro CLI usa permisos IAM de AWS para autenticar y autorizar operaciones. Esta página describe los permisos requeridos para diferentes tipos de usuarios.

---

### Usuarios individuales (ID de constructor/Inicio de sesión social)

Para usuarios individuales que usan Builder ID, Okta o Google/GitHub:
- No se requieren permisos IAM de AWS
- La autenticación se realiza a través del portal de Kiro directamente

---

### Usuarios empresariales (Centro de identidad IAM)

Los usuarios de Enterprise pueden autenticarse con IAM Identity Center. Los administradores asignan permisos a través de la Consola Kiro.

#### Permisos mínimos de usuario

Para que un usuario pueda usar Kiro CLI con Identity Center:

```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": [
      "kiro:SendMessage",
      "kiro:GetSession",
      "kiro:StartSession"
    ],
    "Resource": "*"
  }]
}
```

---

### Permisos de administrador

Ver [Enterprise → IAM →](../14_Enterprise/10_IAM.md) para los permisos mínimos requeridos para administradores que configuran Kiro y suscriben usuarios.

---

### Integración de la CLI de AWS

Cuando usás las herramientas de AWS del CLI de Kiro, se usan las **credenciales AWS configuradas en tu entorno**:

```golpecito
## Kiro usa las credenciales AWS del sistema
exportar AWS_PROFILE=mi-perfil
exportar AWS_DEFAULT_REGION=us-east-1

## O credenciales directas
exportar AWS_ACCESS_KEY_ID=...
exportar AWS_SECRET_ACCESS_KEY=...
```

> Kiro nunca almacena las credenciales AWS — solo las lee del entorno en tiempo de ejecución.

---

### Principio de privilegio mínimo

**Mejores prácticas para el uso de Kiro con AWS:**

1. Usá **IAM roles con permisos mínimos** para las operaciones que Kiro puede realizar
2. Para testing, usamos cuentas AWS separadas de producción
3. Habilitá **MFA** en tu cuenta de AWS
4. Revise periódicamente qué comandos AWS está ejecutando Kiro mediante los **logs de auditoría**
5. En Enterprise, use la Kiro Console para controlar qué herramientas AWS pueden usar los usuarios

---

### Relacionado

- [IAM empresarial →](../14_Enterprise/10_IAM.md)
- [Consideraciones de seguridad →](../03_Chat/12_Consideraciones de seguridad.md)
- [Documentación de AWS IAM →](https://docs.aws.amazon.com/iam/latest/userguide/)

---

*📂 Capítulo: **Privacy and security > Firewalls, proxies, and data perimeters***

## Firewalls, proxies y perímetros de datos

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/firewalls-proxies/](https://kiro.dev/docs/cli/privacy-and-security/firewalls-proxies/)

---

### Descripción general

Si tu organización utiliza firewalls, proxies corporativos o perímetros de datos, necesitarás configurarlos para permitir el tráfico de Kiro CLI.

---

### Puntos finales requeridos

Permitir el acceso a los siguientes dominios:

| Dominio | Puerto | Propósito |
|---|---|---|
| `*.kiro.dev` | 443 (HTTPS) | API principal y autenticación |
| `*.amazonaws.com` | 443 (HTTPS) | Servicios backend de AWS |
| `*.awsapps.com` | 443 (HTTPS) | Centro de Identidad IAM (Empresa) |

---

### Configuración del proxy HTTP/HTTPS

Kiro CLI respeta las variables de entorno estándar de proxy:

```golpecito
## Proxy HTTP
exportar HTTP_PROXY=http://proxy.company.com:8080
exportar HTTPS_PROXY=http://proxy.company.com:8080

## Excluir dominios del proxy
exportar NO_PROXY=localhost,127.0.0.1,.empresa.internal

## Variantes en minúsculas (también soportadas)
exportar http_proxy=http://proxy.company.com:8080
exportar https_proxy=http://proxy.company.com:8080
```

---

### Inspección de certificados SSL/TLS

Si tu organización usa inspección de SSL/TLS (man-in-the-middle), podrías necesitar:

1. Agregar el certificado root de tu proxy al store de certificados del sistema
2. O configurar la variable de entorno:
```golpecito
exportar SSL_CERT_FILE=/ruta/a/corporate-ca.pem
exportar NODE_EXTRA_CA_CERTS=/ruta/a/corporate-ca.pem
```

---

### Perímetros de datos (empresarial)

Para organizaciones que requieren que todo el tráfico permanezca dentro de la red de AWS, Kiro soporta **VPC Endpoints (AWS PrivateLink)**.

Consulte [Puntos finales de VPC →](./06_Puntos finales de VPC (AWS PrivateLink).md) para configurar detalladamente.

---

### Solución de problemas de conectividad

```golpecito
## Verificar que podés acceder a la API de Kiro
rizo -v https://api.kiro.dev/health

## Verificar con proxy explícito
curl -v --proxy http://proxy.company.com:8080 https://api.kiro.dev/health

## Diagnóstico completo
kiro-cli doctor --todos
```

---

### Reglas comunes de firewall

```
## Regla de ejemplo para firewall corporativo (IPv4)
ALLOW TCP 443 -> *.kiro.dev
ALLOW TCP 443 -> *.amazonaws.com
ALLOW TCP 443 -> *.awsapps.com     # Solo Enterprise
```

---

*📂 Capítulo: **Privacy and security > VPC endpoints (AWS PrivateLink)***

## Puntos de enlace de la VPC (AWS PrivateLink)

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/vpc-endpoints/](https://kiro.dev/docs/cli/privacy-and-security/vpc-endpoints/)

---

### Descripción general

**AWS PrivateLink** permite que Kiro CLI se comunique con los servicios de AWS sin que el tráfico salga a Internet público. Ideal para organizaciones con requisitos estrictos de seguridad y perímetros de datos.

---

### Beneficios

- **Sin exposición a Internet** — El tráfico permanece dentro de la red de AWS
- **Superficie de ataque reducida** — Sin rutas públicas de red
- **Cumplimiento** — Facilitar el cumplimiento de las regulaciones de residencia de datos
- **Menor latencia** — Comunicación más rápida dentro de la misma región

---

### Requisitos previos

- Cuenta de AWS con acceso a VPC
- Suscripción Kiro Enterprise
- VPC configurada en la región donde está tu perfil Kiro

---

### Pasos de configuración

#### 1. Cree el punto final de la VPC

```bash
aws ec2 create-vpc-endpoint \
  --vpc-id vpc-xxxxxxxx \
  --service-name com.amazonaws.us-east-1.kiro \
  --vpc-endpoint-type Interface \
  --subnet-ids subnet-xxxxxxxx \
  --security-group-ids sg-xxxxxxxx
```

#### 2. Configurar la resolución DNS

Habilitar **DNS privado** para que el endpoint resuelva el dominio de Kiro automáticamente:

```bash
aws ec2 modify-vpc-endpoint \
  --vpc-endpoint-id vpce-xxxxxxxx \
  --private-dns-enabled
```

#### 3. Actualizar grupos de seguridad

Asegúrese de que el grupo de seguridad del endpoint permita el tráfico desde las instancias que usan Kiro CLI:

```
Inbound:  TCP 443 from your instances/subnets
Outbound: TCP 443 to Kiro service
```

---

### Verificación

```golpecito
## Verificar que el tráfico va por el endpoint privado
kiro-cli doctor --todos

## Ver el punto final configurado
aws ec2 describe-vpc-endpoints --filters "Nombre=nombre-servicio,Valores=*kiro*"
```

---

### Arquitectura de red

```
[Kiro CLI] → [VPC Subnet] → [VPC Endpoint] → [AWS PrivateLink] → [Kiro Service]
                                                    ↑
                                            Sin salida a Internet
```

---

### Notas de administración empresarial

Los administradores Enterprise pueden forzar el uso de puntos finales de VPC para todos los usuarios de su organización desde la **Kiro Console → Configuración**.

---

### Relacionado

- [Firewalls y Proxies →](./05_Firewalls, proxies y perímetros de datos.md)
- [Gobierno empresarial →](../14_Enterprise/06_Governance.md)
- [Documentación de AWS PrivateLink →](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html)

---

*📂 Capítulo: **Reference > CLI commands***

## Referencia de comandos CLI

> **Fuente:** [kiro.dev/docs/cli/reference/cli-commands/](https://kiro.dev/docs/cli/reference/cli-commands/)

---

### Argumentos globales

Estos argumentos funcionan con cualquier comando de Kiro CLI:

| Bandera | Descripción |
|---|---|
| `--verbose` / `-v` / `-vv` / `-vvv` | Nivel de verbosidad de salida |
| `--agente` | Especificar agente a usar |
| `--ayuda` / `-h` | Mostrar ayuda |
| `--versión` / `-V` | Mostrar versión |
| `--ayuda-todos` | Mostrar ayuda extendida |

---

### Comandos

#### `kiro-cli chat`

Iniciar una sesión de chat interactivo. `kiro` es un alias de `kiro-cli chat`.

```bash
kiro-cli chat [OPTIONS] [INPUT]
```

| Argumento | Descripción |
|---|---|
| `--no-interactivo` | Modo no interactivo (para guiones/CI) |
| `--resume` / `-r` | Continuar última sesión |
| `--resume-selector` | Selector para elegir sesión y reanudar |
| `--lista-sesiones` | Listar sesiones guardadas |
| `--lista-modelos` | Listar modelos disponibles |
| `--delete-session <ID>` | Eliminar una sesión |
| `--agente <nombre>` | Usar un agente específico |
| `--trust-all-tools` | Pre-aprobar todas las herramientas |
| `--trust-tools <herramienta>` | Herramientas previas a la aprobación específicas |
| `--require-mcp-startup` | Fallar si un servidor MCP no inicia |
| `--envoltura` | Control de ajuste de palabras: `siempre` / `never` / `auto` |
| `ENTRADA` | Prompt directo (sin modo interactivo) |

```bash
kiro-cli                                              # Chat interactivo
kiro-cli chat "How do I list files?"                 # Pregunta directa
kiro-cli chat --no-interactive --trust-all-tools "Show dir"
kiro-cli chat --resume                               # Retomar sesión
kiro-cli chat --list-models --format json
kiro-cli chat --agent my-agent "Help with AWS CLI"
```

---

#### `agente kiro-cli`

Gestionar configuraciones de agentes.

```bash
kiro-cli agent [SUBCOMMAND] [AGENT_NAME] [OPTIONS]
```

| Subcomando | Descripción |
|---|---|
| `lista` | Listar agentes disponibles |
| `crear <nombre>` | Crear nuevo agente |
| `editar [nombre]` | Editar agente (actual si no se especifica nombre) |
| `validar` | Validar configuración |
| `migrar` | Migrar a nuevo formato |
| `establecido por defecto` | Definir agente por defecto |

```bash
kiro-cli agent list
kiro-cli agent create my-agent
kiro-cli agent edit my-agent
kiro-cli agent set-default backend-specialist
```

---

#### `kiro-cli traducir`

Traducir instrucciones en lenguaje natural a comandos shell ejecutables.

```bash
kiro-cli translate "list all Python files modified last week"
kiro-cli translate -n 3 "search for text in files"   # Mostrar 3 opciones
```

---

#### `kiro-cli mcp`

Gestionar servidores MCP.

| Subcomando | Descripción |
|---|---|
| `mcp add --name <n> --command <cmd> --scope <espacio de trabajo\|global>` | Agregar servidor |
| `mcp eliminar --nombre <n> --scope <alcance>` | Eliminar servidor |
| `lista mcp [espacio de trabajo\|global]` | Listar servidores |
| `mcp import --file <archivo> <alcance>` | Importar configuración |
| `estado de mcp --nombre <n>` | Estado de un servidor |

---

#### `iniciar sesión en kiro-cli`

Autenticar con Kiro CLI.

```bash
kiro-cli login                                           # Abre browser (local) / device code (SSH)
kiro-cli login --license pro --identity-provider <URL> --region us-east-1
kiro-cli login --social google
kiro-cli login --use-device-flow                         # Forzar device flow
```

---

#### `kiro-cli cerrar sesión`

Cerrar sesión. **Termina la sesión en todos los espacios de trabajo** (preserva la configuración y conversaciones guardadas).

```bash
kiro-cli logout
```

---

#### `kiro-cli whoami`

Ver información del usuario autenticado.

```bash
kiro-cli whoami
kiro-cli whoami --format json-pretty
```

---

#### `configuración de kiro-cli`

Gestionar la configuración del CLI.

```bash
kiro-cli settings list                          # Ver todos los settings
kiro-cli settings list --all                    # Ver todos los settings disponibles
kiro-cli settings telemetry.enabled             # Ver un setting
kiro-cli settings telemetry.enabled false       # Setear un setting
kiro-cli settings --delete chat.defaultModel    # Eliminar un setting
kiro-cli settings open                          # Abrir archivo de settings en editor
kiro-cli settings list --format json-pretty
```

---

#### `kiro-cli doctor`

Diagnosticar y solucionar problemas comunes de instalación.

```bash
kiro-cli doctor
kiro-cli doctor --all      # Todos los checks
kiro-cli doctor --strict   # Modo estricto (falla en warnings)
```

---

#### `actualización de kiro-cli`

Actualiza Kiro CLI a la última versión.

```bash
kiro-cli update
kiro-cli update --non-interactive    # Sin commit
```

---

#### `tema kiro-cli`

Cambiar tema visual del menú de autocompletado.

```bash
kiro-cli theme --list
kiro-cli theme dark
kiro-cli theme light
kiro-cli theme system
```

---

#### `integraciones kiro-cli`

Gestionar integraciones del sistema.

```bash
kiro-cli integrations install kiro-command-router   # Instalar kiro command router (v1.26+)
kiro-cli integrations status
kiro-cli integrations uninstall --silent
```

**Kiro Command Router (v1.26+):** permite que `kiro` lance CLI o IDE según tu preferencia.
```golpecito
kiro configurado por defecto cli # kiro → CLI
kiro set-default ide # kiro → IDE
```

---

#### `kiro-cli en línea`

Gestionar sugerencias en línea (texto fantasma).

```bash
kiro-cli inline enable
kiro-cli inline disable
kiro-cli inline status
```

---

#### `diagnóstico kiro-cli`

Generar informe de diagnóstico del sistema.

```bash
kiro-cli diagnostic
kiro-cli diagnostic --format json-pretty
kiro-cli diagnostic --force    # Sin requerir que la app esté corriendo
```

---

#### `problema de kiro-cli`

Cree un problema en GitHub para errores o comentarios.

```bash
kiro-cli issue
kiro-cli issue "Autocomplete not working in zsh"
```

---

#### `versión kiro-cli`

Mostrar versión e información del registro de cambios.

```bash
kiro-cli version
kiro-cli version --changelog
kiro-cli version --changelog=all
kiro-cli version --changelog=1.5.0
```

---

### Gestión de sesiones

```golpecito
## Desde la terminal
kiro-cli chat --list-sessions # Listar sesiones
kiro-cli chat --resume # Retomar última sesión
kiro-cli chat --resume-picker # Picker interactivo de sesiones
kiro-cli chat --delete-session <ID> # Eliminar sesión

## Almacenamiento personalizado
## Por defecto: ~/.kiro/chat-history/
```

---

### Archivos de registro

Los registros se almacenan en `~/.kiro/logs/`. Uso de para depuración:
```golpecito
kiro-cli --verbose chat "..." # -v, -vv, -vvv para más detalles
```

---

*📂 Capítulo: **Reference > Slash commands***

## Referencia de comandos de barra diagonal

> **Fuente:** [kiro.dev/docs/cli/reference/slash-commands/](https://kiro.dev/docs/cli/reference/slash-commands/)

---

### Descripción general

Los comandos de barra diagonal son comandos especiales disponibles dentro de una sesión de chat interactiva. Empiezan con `/` y proporcionan atajos para tareas comunes.

Solo disponibles en **modo interactivo**: `kiro chat > ​​/comando`

---

### Referencia rápida

| comando | Descripción |
|---|---|
| `/ayuda` | Cambiar al Agente de Ayuda o mostrar ayuda |
| `/salir` | Salir de la sesión (alias: `/exit`, `/q`) |
| `/claro` | Limpiar historia de conversación en pantalla |
| `/ contexto` | Gestionar archivos de contexto |
| `/modelo` | Seleccionar modelo de AI |
| `/agente` | Gestionar y cambiar entre agentes |
| `/chat` | Gestionar sesiones de chat |
| `/guardar` | Guardar la conversación |
| `/cargar` | Cargar una conversación guardada |
| `/editor` | Abrir editor externo para el indicador |
| `/responder` | Responder al último mensaje |
| `/punto de control` | Crear/gestionar puntos de control |
| `/plan` | Activar el Plan Agente |
| `/conocimiento` | Gestionar base de conocimientos (experimental) |
| `/ compacto` | Compactar el historial de conversación |
| `/pegar` | Pegar contenido del portapapeles |
| `/herramientas` | Ver y gestionar permisos de herramientas |
| `/solicitudes` | Ver y gestionar avisos |
| `/hooks` | Ver contexto engancha activos |
| `/ uso` | Ver facturación y créditos |
| `/mcp` | Ver servidores MCP cargados |
| `/código` | Gestionar inteligencia de código (LSP) |
| `/experimento` | Alternar funciones experimentales |
| `/ tangente` | Crear punto de control de conversación |
| `/todos` | Ver y gestionar listas TODO |
| `/ problema` | Crear un problema de GitHub |
| `/logdump` | Crear zip con registros para soporte |
| `/ registro de cambios` | Ver registro de cambios del CLI |

---

### Detalle de comandos

#### `/ayuda`

```
> /help                           # Cambiar al Help Agent
> /help How do I configure MCP?   # Pregunta directa al Help Agent
> /help --legacy                  # Texto de ayuda clásico
```

#### `/ contexto`

```
> /context show # Ver configuración y archivos de contexto
> /context agregar src/app.js
> /context agregar "*.py"
> /context agregar "src/**/*.js"
> /context eliminar src/app.js
> /contexto claro
```
> Los cambios NO se conservan entre sesiones. Para hacerlo permanentemente, edite el archivo de configuración del agente.

#### `/modelo`

```
> /modelo # Picker interactivo
> /model claude-opus-4.6 # Selección directa
> /model set-current-as-default # Guardar como predeterminado
```
Soporta tabulación y coincidencia difusa.

#### `/agente`

```
> /agent list
> /agent create my-agent
> /agent create my-agent -D "Code reviewer" -m code-analysis
> /agent create my-agent --manual
> /agent edit                         # Editar agente actual
> /agent edit my-agent
> /agent schema                       # Ver schema de configuración
> /agent set-default my-agent
> /agent swap code-reviewer
```

#### `/herramientas`

```
> /tools                    # Ver todas las tools y permisos
> /tools schema             # Ver input schema de todas las tools
> /tools trust write        # Trust específica para esta sesión
> /tools untrust write      # Volver a solicitar commit
> /tools trust-all          # Trust todas (usar con precaución)
> /tools reset              # Resetear a niveles por defecto
```

Columnas de salida: `~Tokens`, `Permiso` (Confiable/Preguntar/Permitido), `Total`.

#### `/solicitudes`

```
> /prompts list
> /prompts details code-review
> /prompts get code-review [arg]
> @code-review [arg]              # Shortcut directo
> /prompts create my-prompt
> /prompts edit my-prompt
> /prompts remove my-prompt
```

#### `/código`

```
> /code init             # Inicializar LSP para code intelligence
> /code init -f          # Forzar reinicialización
> /code overview         # Overview del workspace
> /code status           # Estado de LSP servers
> /code logs             # Ver logs LSP
> /code logs -l INFO -n 50
> /code logs -p ./lsp-logs.json
```

#### `/punto de control` (experimental)

```
> /checkpoint list
> /checkpoint expand <tag>
> /checkpoint diff <tag1> [tag2]
> /checkpoint restore [<tag>]
> /checkpoint clean
```

#### `/logdump`

```
> /logdump # Crear registros de chat zip con
> /logdump --mcp # Incluir registros de MCP
```
Crea: `q-logs-AAAA-MM-DDTHH-MM-SSZ.zip`

#### `/todos` (experimental)

```
> /todo
> /todo add "Fix authentication bug"
> /todo complete 1
```

---

### Atajos de teclado (modo interactivo)

| Atajó | Acción |
|---|---|
| `Ctrl+C` | Cancelar entrada real |
| `Ctrl+J` | Insertar nueva línea (mensaje multilínea) |
| `Ctrl+S` | Búsqueda difusa de comandos y archivos de contexto |
| `Ctrl+T` | Alternar modo tangente |
| ` ↑` / `↓` | Navegar historial de comandos |

---

*📂 Capítulo: **Reference > Built-in tools***

## Herramientas integradas

> **Fuente:** [kiro.dev/docs/cli/reference/built-in-tools/](https://kiro.dev/docs/cli/reference/built-in-tools/)

---

### Descripción general

Las herramientas integradas son las capacidades nativas que Kiro CLI puede usar para interactuar con el sistema de archivos, ejecutar comandos, buscar en la web, y más.

---

### Archivo leído

Lee el contenido de archivos locales.

**Opciones de configuración:**
```json
{
  "Configuración de herramientas": {
    "leer": {
      "rutaspermitidas": ["src/**", "docs/**"],
      "rutas denegadas": [".env", "**/*.key"]
    }
  }
}
```

---

### globo

Busca usando archivos patrones glob.

**Opciones de configuración:**
```json
{
  "Configuración de herramientas": {
    "globo": {
      "rutas permitidas": ["./src/**"]
    }
  }
}
```

Ejemplo de uso: `Buscar todos los archivos TypeScript en el directorio src`

---

### grep

Busca texto en archivos usando expresiones regulares.

**Opciones de configuración:**
```json
{
  "Configuración de herramientas": {
    "grep": {
      "rutas permitidas": ["./src/**"],
      "resultados máximos": 100
    }
  }
}
```

---

### Escritura de archivo

Escribe o modifica archivos locales.

**Herramientas de diferenciación personalizadas:** Podés configurar herramientas externas como `delta`, `difftastic`, etc. Ver [Herramientas de diferenciación personalizadas →](../03_Chat/14_Custom diff tools.md).

**Opciones de configuración:**
```json
{
  "Configuración de herramientas": {
    "escribir": {
      "allowedPaths": ["src/**", "pruebas/**", "Cargo.toml"],
      "deniedPaths": [".env", "**/*.lock"]
    }
  }
}
```

---

### Ejecutar comandos de Shell

Ejecuta comandos shell en el sistema.

**Opciones de configuración:**
```json
{
  "Configuración de herramientas": {
    "cáscara": {
      "allowedCommands": ["estado de git", "prueba npm", "construcción de carga"],
      "deniedCommands": ["rm -rf .*", "sudo .*"],
      "autoAllowReadonly": verdadero
    }
  }
}
```

> `autoAllowReadonly: true` — preaprueba automáticamente comandos de solo lectura.

---

### Ejecutar comandos de AWS

Permite ejecutar comandos de AWS CLI directamente. Requiere que `aws-cli` esté instalado y configurado.

```
"Run aws s3 ls to list my buckets"
"Check the status of my CloudFormation stack"
```

---

### Búsqueda y recuperación web

#### búsqueda_web
Busca información en la web.

#### web_fetch
Obtiene contenido de URL específicas.

**Modos de búsqueda:**
| Modo | Descripción |
|---|---|
| `auto` | Kiro elige el mejor modo |
| `crudo` | HTML sin procesar |
| `texto` | Texto plano extraido |
| `markdown` | Convertir a Markdown |

**Configuración:**
```json
{
  "Configuración de herramientas": {
    "web_search": { "habilitado": verdadero },
    "web_fetch": { "habilitado": verdadero }
  }
}
```

**Limitaciones:**
- No puede acceder a páginas que requieren autenticación
- Algunas páginas pueden bloquear el acceso programático
- Se pueden aplicar límites de tarifas

---

### Introspeccione las capacidades de Kiro CLI

Herramienta que permite a Kiro responder preguntas sobre sus propias capacidades, configuración y estado.

**Preguntas de ejemplo:**
- "¿Cuáles son los comandos disponibles?"
- "¿Cómo configurar un servidor MCP?"
- "¿Qué agente estoy usando actualmente?"

---

### Inteligencia de código

Integración con Language Server Protocol (LSP) para análisis de código avanzado:
- Información de desplazamiento
- Ir a la definición
- Encuentra referencias
- Diagnóstico de código

Inicializar con `/code init` en el chat.

---

### Delegar tareas (experimental)

Permite lanzar tareas asíncronas en segundo plano. Ver [Delegar →](../09_Experimental/06_Delegate.md).

---

### Enviar problema/solicitud de función

Herramienta para crear issues en GitHub directamente desde el chat. También disponible como `/issue`.

---

### Herramienta de conocimiento (experimental)

Acceso a la base de conocimiento para búsqueda semántica persistente. Ver [Gestión del Conocimiento →](../09_Experimental/01_Gestión del Conocimiento.md).

---

### Herramienta de pensamiento (experimental)

Muestra el proceso de razonamiento de la IA paso a paso. Ver [Herramienta de pensamiento →](../09_Experimental/04_Thinking tool.md).

---

### Herramienta de lista de tareas pendientes (experimental)

Gestión de listas de tareas persistentes. Ver [Listas TODO →](../09_Experimental/03_TODO listas.md).

---

### Permisos de herramientas

Por defecto, Kiro solicita commit para herramientas que pueden modificar el sistema:

| Herramienta | Permiso por defecto |
|---|---|
| `leer` | Auto aprobado |
| `globo` | Auto aprobado |
| `grep` | Auto aprobado |
| `escribir` | Requiere commit |
| `cáscara` | Requiere commit |
| `aws` | Requiere commit |
| `búsqueda_web` | Auto aprobado |
| `web_fetch` | Auto aprobado |

Gestioná permisos con `/tools trust`, `/tools untrust`, `/tools trust-all`.

---

### Uso de la configuración de herramientas en la configuración del agente

```json
{
  "toolsSettings": {
    "write": { "allowedPaths": ["src/**"] },
    "shell": {
      "allowedCommands": ["git status", "npm test"],
      "autoAllowReadonly": true
    },
    "@custom-mcp/my_tool": {
      "custom_param": "value"
    }
  }
}
```

---

*📂 Capítulo: **Reference > Exit codes***

## Códigos de salida

> **Fuente:** [kiro.dev/docs/cli/reference/exit-codes/](https://kiro.dev/docs/cli/reference/exit-codes/)

---

### Referencia del código de salida

| Código | SIGNIFICADO |
|---|---|
| **0** | Éxito — La tarea se completó correctamente |
| **1** | Errores generales |
| **2** | Error de uso / argumentos inválidos |
| **3** | Servidor(es) MCP fallaron al iniciar |

---

### Requerir servidores MCP

Por defecto, los fallos de los servidores MCP se loguean como advertencias **sin afectar el código de salida**. Usaremos `--require-mcp-startup` para fallar inmediatamente cuando los servidores MCP son críticos:

```bash
kiro-cli chat --require-mcp-startup --no-interactive "Run task"
```

Si **cualquier** servidor MCP configurado falla al iniciar, el CLI termina inmediatamente con el código `3`.

> Usá `--require-mcp-startup` en pipelines CI/CD donde las herramientas MCP son esenciales. Esto previene fallas silenciosas donde las tareas se completan sin el utillaje esperado.

---

### Códigos de salida del gancho

Los [Hooks](../03_Chat/../08_Hooks/01_Overview.md) usan un conjunto separado de códigos de salida para controlar la ejecución de herramientas:

| Código | Comportamiento en Hook |
|---|---|
| **0** | Gancho completado exitosamente, continuar |
| **≠ 0** | Hook falló — para hooks `preToolUse`, **bloquea** la ejecución de la herramienta |

---

### Ejemplos de secuencias de comandos

#### Script de bash

```golpecito
##!/bin/bash
chat kiro-cli \
  --require-mcp-inicio \
  --no-interactivo \
  --confiar en todas las herramientas \
  "Ejecutar análisis"

código_salida=$?

caso $código_salida en
  0)
    echo " ✅ Éxito "
    ;;
  3)
    echo "❌ Los servidores MCP no pudieron iniciarse"
    salida 1
    ;;
  *)
    echo "❌ Error con el código $exit_code"
    salir $código_salida
    ;;
esac
```

#### Canalización de CI/CD (acciones de GitHub)

```yaml
- name: Run Kiro task
  run: |
    kiro-cli chat \
      --require-mcp-startup \
      --no-interactive \
      --trust-all-tools \
      "Analyze code quality"
  continue-on-error: false
```

#### Canalización de CI/CD (GitLab CI)

```yaml
kiro-analysis:
  script:
    - kiro-cli chat --require-mcp-startup --no-interactive "Run tests"
  allow_failure: false
```

---

### Mejores prácticas

- Usaremos `--require-mcp-startup` en CI/CD cuando tus tareas dependen de las herramientas MCP
- Agregará el registro detallado (`-v` o `-vv`) cuando estés depurando códigos de salida
- Verificará los códigos de salida explícitamente en lugar de depender del comportamiento implícito del shell
- Separar los fallos de MCP de los fallos generales para proporcionar mejores mensajes de error

---

*📂 Capítulo: **Reference > Settings***

## Referencia de configuración

> **Fuente:** [kiro.dev/docs/cli/reference/settings/](https://kiro.dev/docs/cli/reference/settings/)

---

### Accediendo a la configuración

```bash
kiro-cli settings list                          # Settings actuales
kiro-cli settings list --all                    # Todos los disponibles
kiro-cli settings <key>                         # Ver valor de un setting
kiro-cli settings <key> <value>                 # Setear un setting
kiro-cli settings --delete <key>                # Eliminar un setting
kiro-cli settings open                          # Abrir archivo en editor
kiro-cli settings list --format json-pretty     # Output JSON
```

**Archivo de configuración:** `~/.kiro/settings/cli.json`

---

### Referencia de configuración

#### Telemetría y Privacidad

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `telemetría.habilitada` | `verdadero` | Habilitar/deshabilitar telemetría |
| `telemetríaClientId` | `"cliente-123"` | ID de cliente para telemetría |

```bash
kiro-cli settings telemetry.enabled false    # Deshabilitar telemetría
```

---

#### Interfaz de chat

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `chat.defaultModel` | `"claude-3-soneto"` | Modelo por defecto |
| `chat.defaultAgent` | `"mi-agente"` | Agente por defecto |
| `chat.diffTool` | `"delta"` | Herramienta diferencial externa |
| `chat.saludo.habilitado` | `falso` | Mostrar/ocultar saludo inicial |
| `chat.editMode` | `verdadero` | Modo edición en línea |
| `chat.enableNotificaciones` | `verdadero` | Notificaciones del sistema |
| `chat.disableMarkdownRendering` | `falso` | Deshabilitar render de Markdown |
| `chat.disableAutoCompaction` | `verdadero` | Deshabilitar compactación automática |
| `compactación.excludeMessages` | `2` | Mensajes a eliminar de compactación |
| `compactation.excludeContextWindowPercent` | `2` | % de ventana de contexto a eliminar |
| `chat.enablePromptHints` | `falso` | Mostrar sugerencias de indicaciones |
| `chat.enableHistoryHints` | `verdadero` | Mostrar pistas del historial |
| `chat.uiMode` | `"compacto"` | Modo UI (`compacto` / `predeterminado`) |
| `chat.enableContextUsageIndicator` | `verdadero` | Indicador de uso de contexto |

---

#### Base de conocimientos (experimental)

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `chat.enableKnowledge` | `verdadero` | Habilitar base de conocimientos |
| `knowledge.defaultIncludePatterns` | `'["*.py", "*.js"]'` | Patrones de archivos a incluir |
| `knowledge.defaultExcludePatterns` | `'["*.log", "node_modules"]'` | Patrones a eliminar |
| `conocimiento.maxFiles` | `1000` | Máximo de archivos a indexar |
| `conocimiento.chunkSize` | `512` | Tamaño de trozo para indexado |
| `conocimiento.chunkOverlap` | `50` | Superposición entre trozos |
| `conocimiento.tipo de índice` | `"rápido"` | Tipo de índice: `"mejor"` / `"rápido"` |

---

#### Atajos de teclas

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `chat.skimCommandKey` | `"f"` | Tecla para modo skim |
| `chat.autocompletionKey` | `"Pestaña"` | Tecla de autocompletado |
| `chat.tangentModeKey` | `"t"` | Tecla para modo tangente |
| `chat.delegateModeKey` | `"d"` | Tecla para modo delegar |

---

#### Alternancia de funciones (experimental)

| Configuración | comando | Descripción |
|---|---|---|
| `chat.enableThinking` | `kiro-cli configuración chat.enableThinking true` | Herramienta de pensamiento |
| `chat.enableTangentMode` | `kiro-cli configuración chat.enableTangentMode true` | Modo tangente |
| `chat.enableTodoList` | `kiro-cli configuración chat.enableTodoList verdadero` | Listas de tareas pendientes |
| `chat.enableCheckpoint` | `configuración de kiro-cli chat.enableCheckpoint verdadero` | Puntos de control |
| `chat.enableDelegate` | `kiro-cli configuración chat.enableDelegate true` | Delegar tareas |
| `introspect.tangentMode` | `Configuración de kiro-cli introspect.tangentMode true` | Tangente en introspección |

---

#### API y servicio

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `api.tiempo de espera` | `30` | Timeout en segundos para solicitudes a la API |

---

#### Protocolo de contexto modelo (MCP)

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `mcp.initTimeout` | `10` | Timeout de inicialización del servidor MCP |
| `mcp.noInteractiveTimeout` | `5` | Timeout en modo no interactivo |
| `mcp.loadedBefore` | `verdadero` | Bandera de inicialización previa |

---

### Ejemplos de configuración comunes

#### Configuración básica

```bash
kiro-cli settings telemetry.enabled false
kiro-cli settings chat.defaultModel "claude-3-sonnet"
kiro-cli settings chat.greeting.enabled false
```

#### Habilitar funciones experimentales

```bash
kiro-cli settings chat.enableThinking true
kiro-cli settings chat.enableTangentMode true
kiro-cli settings chat.enableTodoList true
kiro-cli settings chat.enableCheckpoint true
kiro-cli settings chat.tangentModeKey "t"
kiro-cli settings chat.delegateModeKey "d"
```

#### Configuración de la base de conocimientos

```bash
kiro-cli settings chat.enableKnowledge true
kiro-cli settings knowledge.defaultIncludePatterns '["*.py", "*.js", "*.md"]'
kiro-cli settings knowledge.defaultExcludePatterns '["*.log", "node_modules", ".git"]'
kiro-cli settings knowledge.maxFiles 2000
```

#### Ajuste de rendimiento

```bash
kiro-cli settings api.timeout 60                           # Para conexiones lentas
kiro-cli settings knowledge.chunkSize 1024
kiro-cli settings chat.disableAutoCompaction true          # Conservaciones largas
```

---

### Configuración de solución de problemas

```golpecito
## Valores inválidos
lista de configuraciones de kiro-cli --all # Ver todos los valores válidos

## Restablecer una configuración
configuración de kiro-cli --eliminar <clave>

## Verificar archivo de configuración
gato ~/.kiro/settings/cli.json

## Editar directamente (solo si sabés lo que haces)
configuración de kiro-cli abierta
```

---

### Variables de entorno

| Variables | Descripción |
|---|---|
| `KIRO_LOG_NO_COLOR=1` | Deshabilitar colores en registros |

---

### Archivo de configuración

Los ajustes se almacenan en JSON en `~/.kiro/settings/cli.json`.

> Se recomienda usar `kiro-cli settings` para hacer cambios — proporciona validación automática.

---

*📂 Capítulo: **Upgrading from Q CLI***

## Actualización desde la CLI para desarrolladores de Amazon Q

> **Fuente:** [kiro.dev/docs/cli/migrating-from-q/](https://kiro.dev/docs/cli/migrating-from-q/)

---

### Descripción general

Kiro CLI es la **próxima evolución de Q CLI**. Tus flujos de trabajo existentes, suscripción y autenticación continúan funcionando sin ningún cambio.

- Disponible desde el **17 de noviembre de 2025**
- El **24 de noviembre de 2025**, Q Developer CLI con actualización automática habilitada se actualizó automáticamente a Kiro CLI
- Si tenías la actualización automática deshabilitada, actualizá manualmente: `q update` o "Check for update" en la aplicación Amazon Q

---

### Diferencias clave

| Característica | CLI para desarrolladores de Amazon Q | Kiro CLI |
|---|---|---|
| **Nombre del binario** | `q` / `q chat` | `kiro-cli` / `kiro-cli chat` (retrocompatible con `q`) |
| **Autenticación** | ID de constructor + Centro de identidad IAM | ID de constructor + Centro de identidad IAM + **Google + GitHub** |
| **Agente por defecto** | `q_default` | `kiro_default` |
| **Carpeta de configuración** | `~/.aws/amazonq/` | `~/.kiro/` |
| **Steering/Reglas** | `~/.aws/amazonq/rules/` | `~/.kiro/steering/` |
| **Nombres de herramientas** | `fs_read`, `fs_write`, `execute_bash`, `use_aws`, `report_issue` | `leer`, `escribir`, `shell`, `aws`, `report` (retrocompatibles) |
| **Licencia del software** | Apache 2.0 | Licencia de propiedad intelectual de AWS |
| **Registros** | Varia | `$TMPDIR/kiro-log` |

---

### Migración única durante la instalación

Al instalar Kiro CLI por primera vez, se ejecuta una **migración automática**:

1. Prompts y agentes de `~/.aws/amazonq/` se copian a `~/.kiro/` con los mismos nombres
2. Configure MCP de `~/.aws/amazonq/mcp.json` se copia a `~/.kiro/settings/mcp.json` (los conflictos se saltan)  
3. Archivos de `~/.aws/amazonq/rules/` se copian a `~/.kiro/steering/` con los mismos nombres
4. Se crea un `cli.json` con la configuración de Q Developer CLI
5. Kiro CLI **continúa leyendo la carpeta `.amazonq`** en tus proyectos — tus reglas, agentes y configuraciones de MCP existentes siguen funcionando

> Si guardas nuevas configuraciones de avisos o agentes, se guardan en la carpeta `.kiro` del proyecto. Si existen ambas carpetas, lee desde `.kiro`.

---

### Rutas del archivo de configuración

| Configuración | CLI de desarrollador Q | Kiro CLI |
|---|---|---|
| PCM (global) | `~/.aws/amazonq/mcp.json` | `~/.kiro/settings/mcp.json` |
| MCP (espacio de trabajo) | `.amazonq/mcp.json` | `.kiro/settings/mcp.json` |
| Avisos (globales) | `~/.aws/amazonq/prompts/` | `~/.kiro/prompts/` |
| Mensajes (espacio de trabajo) | `.amazonq/prompts/` | `.kiro/prompts/` |
| Agentes (globales) | `~/.aws/amazonq/cli-agents/` | `~/.kiro/agents/` |
| Agentes (espacio de trabajo) | `.amazonq/cli-agents/` | `.kiro/agentes/` |
| Steering/Reglas (global) | `~/.aws/amazonq/rules/` | `~/.kiro/steering/` |
| Steering/Reglas (espacio de trabajo) | `.amazonq/rules/` | `.kiro/steering/` |
| Configuración | — | `~/.kiro/settings/cli.json` |

---

### Cambios importantes

- **Kiro CLI no modifica tus carpetas `.amazonq` existentes**
- La autenticación y gestión de suscripción usan el **portal web de Kiro**
- Los registros se escriben en `$TMPDIR/kiro-log`
- Los nombres de herramientas son diferentes pero **retrocompatibles** — tus agentes personalizados existentes siguen funcionando
- El agente por defecto cambió a `kiro_default`. En `/agent list` aparece con "No se encontró ruta" porque la configuración está en memoria
- La interfaz de usuario tiene colores y nombres actualizados.
- El agente por defecto soporta tanto **Amazon Q Rules** como **Kiro Steering**
- Si tu proyecto tiene ambas carpetas `.kiro` y `.amazonq`, la configuración se carga desde `.kiro` (verás una advertencia al iniciar sesión)

---

### Preguntas frecuentes

**¿Kiro CLI es retrocompatible con Q Developer CLI?**
Sí. Podés continuar usando los puntos de entrada `q` y `q chat`. Toda la funcionalidad de Q Developer CLI está disponible en Kiro CLI.

**¿Tengo que cambiar mis scripts de automatización?**
No. Kiro CLI es retrocompatible. Los viejos nombres de herramientas (`fs_read`, `fs_write`, etc.) siguen funcionando.

**¿Puedo usar Kiro CLI con mi suscripción Q Developer Pro?**
Sí. Kiro CLI funciona con tu suscripción Q Developer Pro.

**¿Deberías migrar a un plan Kiro?**
Kiro ofrece 3 niveles que mejor mapean a las necesidades del desarrollador, y **cada nivel soporta excedentes** — algo que no está disponible en Q Developer Pro.

**¿Kiro usa mi contenido para entrenar modelos?**
Ver [Protección de datos →](./16_Privacy%20and%20security/01_Data%20protection.md) y la sección de mejora del servicio.

**¿La aplicación de indemnización de salida se actualiza de Q Developer Pro?**
Sí, los suscriptores de pagos de Kiro tienen indemnización de salida, igual que los usuarios de Q Developer Pro. Ver Sección 50.10 de los Términos de Servicio.

---

### Obtener ayuda

Si encuentras problemas durante la migración:

1. Revisar [Referencia de comandos CLI →](./17_Reference/01_CLI%20commands.md)
2. Revisar [Solución de problemas →](./15_Troubleshooting.md)
3. Contactar soporte desde el tablero de Kiro

---

### Próximos pasos

- [Funciones de chat →](./03_Chat/)
- [Agentes personalizados →](./04_Custom%20agents/)
- [Integración MCP →](./05_MCP/)
- [Agente Hooks →](./07_Hooks.md)
- [Referencia de configuración →](./17_Reference/05_Settings.md)