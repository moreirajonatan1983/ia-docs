# Manual Consolidado: Kiro Autonomous

> Este documento es una consolidación extensa y detallada de toda la documentación referida a esta herramienta.



---

*📂 Capítulo: **Get started > Setup***

## Configuración: Agente autónomo

> **Fuente:** [kiro.dev/docs/autonomous-agent/setup/](https://kiro.dev/docs/autonomous-agent/setup/)
> **Estado:** Vista previa

---

Comenzá con el Kiro Autónomo Agente conectando tu cuenta de GitHub y configurando el acceso a tus repositorios.

---

### Requisitos previos

- Una cuenta de Kiro activa
- Cuenta de GitHub con permisos de escritura en los repositorios que quieres usar
- La aplicación Kiro Agent GitHub instalada en tu organización o cuenta personal (lo hace un propietario)

---

### Pasos

#### 1. Aplicación web Ir al

Navegá a [app.kiro.dev/agent](https://app.kiro.dev/agent) para acceder al Agente Autónomo.

#### 2. Iniciar sesión

Ingresá con tu cuenta de Kiro existente.

#### 3. Vincular tu cuenta de GitHub

Conecta tu cuenta de GitHub para darle al agente acceso a tus repositorios:

1. Vaya a **Configuración** en la aplicación web
2. Hacer clic en **"Conectar GitHub"**
3. Autorizar la **aplicación Kiro Agent GitHub**
4. Seleccione a qué repositorios puede acceder el agente

> Necesitás tener **permisos de escritura** en los repositorios para que el agente pueda crear sucursales y abrir pull request.

---

### Cómo funciona el acceso al repositorio

Kiro Autónomo Agente muestra todos los repositorios donde se cumplen **ambas condiciones**:

1. Tu usuario de GitHub tiene acceso al repositorio
2. La aplicación Kiro Agent GitHub fue instalada y autorizada para ese repositorio

Esto significa que verás repositorios de cuentas personales, repositorios compartidos y organizaciones — siempre que tanto tu usuario de GitHub como la aplicación Kiro Agent tengan acceso.

---

### Próximos pasos

Una vez que conectaste tu cuenta de GitHub, estás listo para [crear tu primera tarea →](../02_Using%20the%20agent/02_Creating%20tasks.md)

Ver también:
- [Integración de GitHub →](../04_GitHub.md)
- [Usando el agente →](../02_Usando%20the%20agent/)

---

*📂 Capítulo: **Using the agent > Chatting with the agent***

## Chatear con el agente

> **Fuente:** [kiro.dev/docs/autonomous-agent/using-the-agent/chatting/](https://kiro.dev/docs/autonomous-agent/using-the-agent/chatting/)

---

Podés chatear con el Kiro Autónomo Agente para discutir enfoques, hacer preguntas y dar orientación antes y durante la ejecución de tareas.

---

### Antes de crear una tarea

Usa el chat para:
- Discutir diferentes enfoques de implementación
- Aclarar requisitos o restricciones
- Obtener la opinión del agente sobre decisiones técnicas

El agente tiene acceso a **búsqueda web**, **aprendizajes de reseñas de código anteriores**, y **contexto de otras tareas** para proporcionar respuestas informadas.

---

### Durante la ejecución de la tarea

Una vez que se crea una tarea, podrás continuar charlando para:
- Orientar al agente en el enfoque de implementación
- Proveer requisitos o restricciones adicionales
- Pedir al agente que haga más trabajo después de revisar los resultados iniciales.

> **Importante:** Cualquier comentario o dirección actualizará el alcance de la tarea actual. No podrás crear una segunda tarea en el mismo chat — para trabajar en una tarea diferente, iniciará un nuevo chat.

---

### Relacionado

- [Creando tareas →](./02_Creating%20tasks.md)
- [Integración de GitHub →](../04_GitHub.md)

---

*📂 Capítulo: **Using the agent > Creating tasks***

## Creando tareas

> **Fuente:** [kiro.dev/docs/autonomous-agent/using-the-agent/creating-tasks/](https://kiro.dev/docs/autonomous-agent/using-the-agent/creating-tasks/)

---

### Desde app.kiro.dev/agent

Navegá a [app.kiro.dev/agent](https://app.kiro.dev/agent) para iniciar un nuevo chat:

1. Opcionalmente, seleccione múltiples repositorios al iniciar el chat
2. Describí lo que querés que haga el agente
3. Si no seleccionaste repositorios al inicio, se te pedirá que los elijas cuando le pidas al agente que trabaje en algo

El agente analiza tu solicitud, desglosa el trabajo y comienza la ejecución.

> **Tareas de múltiples repositorios:** El Kiro Autónomo Agente puede trabajar en múltiples repositorios en una sola tarea. Cuando asignas trabajo que abarca múltiples repositorios, coordina todos los cambios y abre pull request en cada uno. Solo seleccioná repositorios de confianza, especialmente al mezclar repositorios públicos y privados, ya que el agente aprende y sigue instrucciones en el código del repositorio — incluso si son maliciosas.

---

### De problemas de GitHub

Necesitás [conectar GitHub →](../04_GitHub.md) primero.

**Usando el comando `/kiro`:**  
Mencioná `/kiro` en un comentario de cualquier asunto para asignarle esa tarea al Agente Autónomo Kiro.

**Usando la etiqueta `kiro`:**  
Agrega el label `kiro` a cualquier tema. El Kiro Autónomo Agente comenzará a trabajar en la tarea y escuchará todos los comentarios del problema para contexto o feedback adicional.

---

### Ciclo de vida de la tarea

Las tareas pasan por diferentes estados mientras el agente trabaja:

| Estado | Descripción |
|---|---|
| **En cola** | La tarea está esperando para iniciar. Ocurre cuando alcanzaste el límite de 10 tareas concurrentes. |
| **En progreso** | El agente está trabajando activamente — analizando requisitos, escribiendo código o ejecutando pruebas. |
| **Necesita atención** | La tarea necesita entrada o el agente tiene una pregunta de aclaración. Revise el mensaje del agente y proporcione la información solicitada. |
| **Completado** | El agente terminó el trabajo y abrió pull request. Revisará los cambios y proporcionará comentarios. Dar feedback mueve la tarea a *en cola* y luego a *en progreso* cuando hay un espacio disponible. |
| **Cancelado** | La tarea fue cancelada y no se completará. Las tareas canceladas no pueden reanudarse. |

---

### Consejos para tareas

Siga estas mejores prácticas al crear tareas:

**Sé específico sobre el resultado**  
Describí claramente cómo querés que se vea el resultado final. En lugar de "mejorar el flujo de inicio de sesión", decí "agregar funcionalidad de restablecimiento de contraseña en la página de inicio de sesión con verificación por correo electrónico".

**Describe el problema que estás tratando de resolver**  
Explique el contexto y por qué se necesita el trabajo. Esto ayuda al agente a entender las restricciones y tomar mejores decisiones de implementación.

**Proporcioná contexto relevante**  
Linkeá documentación relacionada, ejemplos, o código existente que deba informar la implementación.

**Definición de criterios de aceptación**  
Lista de condiciones específicas que deben cumplirse para que la tarea se considere completa.

**Usá archivos de Steering**  
El Kiro Self Agent busca automáticamente archivos de Steering en la carpeta `.kiro/steering/` en la raíz de tu repositorio. Estos archivos Markdown definen los estándares, arquitectura y convenciones de tu equipo, asegurando que el agente siga consistentemente tus patrones establecidos. Son especialmente útiles para:
- Convenciones de código
- Patrones arquitectónicos
- Preferencias del stack tecnológico
- Enfoques de prueba

---

### Relacionado

- [Chateando con el agente →](./01_Chatting%20with%20the%20agent.md)
- [Agente Sandbox →](../03_Agent%20Sandbox/)
- [Integración de GitHub →](../04_GitHub.md)

---

*📂 Capítulo: **Agent Sandbox > Internet Access***

## Acceso a Internet: Agente Sandbox

> **Fuente:** [kiro.dev/docs/autonomous-agent/sandbox/internet-access/](https://kiro.dev/docs/autonomous-agent/sandbox/internet-access/)

---

El Agent Sandbox puede configurarse con diferentes niveles de acceso a Internet según tus necesidades de seguridad y dependencias del proyecto.

---

### Niveles de acceso

#### 1. Sólo acceso a conexiones *(más seguro)*

El nivel mínimo requerido para que el sandbox funcione. Permite al agente:
- Clonar repositorios de GitHub
- Abrir y actualizar pull requests
- Acceder a GitHub a través del servicio gateway de Kiro

> **Recomendado** cuando tus tareas no requieren dependencias externas.

---

#### 2. Dependencias comunes

Incluye acceso a conexiones **más** registros de paquetes comunes y herramientas de desarrollo. Permite instalar dependencias desde administradores de paquetes populares sin requerir acceso completo a Internet.

**Dominios permitidos automáticamente:**

```
alpinelinux.org  amazonaws.com  anaconda.com  apache.org  apt.llvm.org
archlinux.org  aws.amazon.com  azure.com  bitbucket.org  bower.io
centos.org  cocoapods.org  continuum.io  cpan.org  crates.io
debian.org  docker.com  docker.io  dot.net  dotnet.microsoft.com
eclipse.org  fedoraproject.org  gcr.io  ghcr.io  github.com
githubusercontent.com  gitlab.com  golang.org  google.com  goproxy.io
gradle.org  hashicorp.com  haskell.org  hex.pm  java.com  java.net
jcenter.bintray.com  json-schema.org  json.schemastore.org  k8s.io
launchpad.net  maven.org  mcr.microsoft.com  metacpan.org  microsoft.com
nodejs.org  npmjs.com  npmjs.org  nuget.org  oracle.com  packagecloud.io
packages.microsoft.com  packagist.org  pkg.go.dev  ppa.launchpad.net
pub.dev  pypa.io  pypi.org  pypi.python.org  pythonhosted.org  quay.io
ruby-lang.org  rubyforge.org  rubygems.org  rubyonrails.org  rustup.rs
rvm.io  sourceforge.net  spring.io  swift.org  ubuntu.com
visualstudio.com  yarnpkg.com
```

---

#### 3. Abrir Internet

Proporciona acceso irrestricto a Internet al sandbox.

> ⚠️ **Advertencia de seguridad:** Habilitar permisos de red exponen tu entorno a riesgos de seguridad, incluyendo: ataques de inyección rápida, extracción de código y secretos, introducción de malware o fallas de seguridad, y uso de contenido que podría violar términos de licencia. Consideré cuidadosamente estos riesgos antes de habilitarlo.

---

#### 4. Lista de permitidos personalizada

Especificá una lista de dominios permitidos separados por coma. Usaremos el formato `.domain` para incluir todos los subdominios.

**Ejemplos:**

| Entrada | Qué permite |
|---|---|
| `api.ejemplo.com` | Solo ese dominio específico |
| `.ejemplo.com` | `example.com` y todos sus subdominios (`api.example.com`, `www.example.com`, etc.) |
| `api.ejemplo.com, .cdn.ejemplo.com` | Múltiples dominios y patrones de subdominio |

---

### Relacionado

- [Variables de entorno →](./02_Environment%20Variables.md)
- [Configuración del entorno →](./04_Environment%20Configuration.md)

---

*📂 Capítulo: **Agent Sandbox > Environment Variables***

## Variables de entorno: Agente Sandbox

> **Fuente:** [kiro.dev/docs/autonomous-agent/sandbox/environment-variables/](https://kiro.dev/docs/autonomous-agent/sandbox/environment-variables/)

---

### Variables de entorno

Configure variables de entorno que estarán disponibles para el agente durante la ejecución de tareas. Son útiles para **valores de configuración que no son sensibles**.

Las variables de entorno se configuran desde [app.kiro.dev/agent/settings](https://app.kiro.dev/agent/settings) bajo **Sandbox → Variables de entorno**.

---

### Secretos

Gestioná credenciales sensibles y claves API de forma segura en el sandbox.

**Características:**
- Los secretos están **cifrados en reposo**
- Se exponen como variables de entorno en el sandbox aislado durante la ejecución de tareas
- Solo se descifran dentro del entorno aislado

> ⚠️ **Advertencia de seguridad:** El agente puede exfiltrar estos secretos a través de cambios de código, registros o solicitudes externas. Solo proporcionalá los secretos necesarios para la tarea y solo usará el agente con repositorios de confianza.

---

### Claves duplicadas

Si la misma clave existe tanto en variables de entorno como en secretos, **el valor de la variable de entorno tiene precedencia**.

---

### Uso de variables en la configuración de MCP

Puedes referenciar variables de entorno y secretos en tu configuración MCP usando la sintaxis `${key_name}`:

```json
{
  "mcpServers": {
    "server-name": {
      "command": "executable",
      "args": ["arg1", "arg2"],
      "env": {
        "ENV_VAR_KEY": "${my_env_var_key}",
        "SECRET_KEY":  "${my_secret_key}"
      }
    }
  }
}
```

Los valores se resuelven cuando se inicia el sandbox.

---

### Relacionado

- [MCP en Sandbox →](./03_MCP.md)
- [Acceso a Internet →](./01_Internet%20Access.md)

---

*📂 Capítulo: **Agent Sandbox > MCP***

## MCP: Agente Sandbox

> **Fuente:** [kiro.dev/docs/autonomous-agent/sandbox/mcp/](https://kiro.dev/docs/autonomous-agent/sandbox/mcp/)

---

Los servidores MCP (Model Context Protocol) pueden configurarse en el sandbox del Agente Autónomo para ampliar sus capacidades con herramientas externas.

---

### Configuración

Los servidores MCP se configuran en el archivo de configuración MCP del sandbox. La configuración se carga cuando el sandbox inicia y permanece disponible durante toda la ejecución de la tarea.

#### Ejemplo de configuración

```json
{
  "mcpServers": {
    "aws-knowledge-mcp-server": {
      "command": "uvx",
      "args": [
        "fastmcp",
        "run",
        "https://knowledge-mcp.global.api.aws"
      ],
      "env": {}
    }
  }
}
```

---

### Servidores compatibles

> **Limitación actual:** Solo se soportan **servidores locales MCP**. Los servidores MCP remotos no están disponibles en este momento.

---

### Uso de variables y secretos de entorno

Podés referenciar [variables de entorno y secretos](./02_Environment%20Variables.md) en tu configuración MCP para pasar credenciales y valores de configuración de forma segura.

Usaremos la sintaxis `${key_name}` para referenciar las claves:

```json
{
  "mcpServers": {
    "server-name": {
      "command": "executable",
      "args": ["arg1", "arg2"],
      "env": {
        "ENV_VAR_KEY": "${my_env_var_key}",
        "SECRET_KEY":  "${my_secret_key}"
      }
    }
  }
}
```

Tanto las variables de entorno como los secretos usan la misma sintaxis. Los valores se resuelven cuando se inicia el sandbox.

---

### Relacionado

- [Variables de entorno →](./02_Environment%20Variables.md)
- [Configuración del entorno →](./04_Environment%20Configuration.md)

---

*📂 Capítulo: **Agent Sandbox > Environment Configuration***

## Configuración del entorno: Agente Sandbox

> **Fuente:** [kiro.dev/docs/autonomous-agent/sandbox/environment-configuration/](https://kiro.dev/docs/autonomous-agent/sandbox/environment-configuration/)

---

El sandbox del Agente Autónomo puede configurarse usando un `Dockerfile` para que el entorno coincida exactamente con los requisitos de tu proyecto.

---

### Configuración automática

Kiro Autónoma Agent busca un `Dockerfile` en la **raíz de tu repositorio**. Si lo encuentra, el agente configura automáticamente el sandbox basándose en esas especificaciones.

> **Limitación:** Solo se soportan imágenes de contenedores **disponibles públicamente**. Las imágenes de registros privados y repositorios privados no pueden ser accedidas por el sandbox.

---

### Configuración del archivo Docker

Podés usar un [Dockerfile](https://docs.docker.com/reference/dockerfile/) estándar para configurar el entorno del sandbox. El agente construirá y usará la imagen Docker definida en tu Dockerfile.

#### Ejemplo de archivo Docker

```archivo docker
DESDE el nodo:18

DIRTRABAJO /aplicación

## Instalar dependencias
COPIAR paquete*.json ./
EJECUTAR instalación npm

## Copiar el código de la aplicación
COPIAR. .

## Establecer variables de entorno
ENV NODE_ENV=producción

## Exponer puerto
EXPONER 3000

## Comando de inicio
CMD ["npm", "inicio"]
```

---

### Casos de uso

- Asegurar que las mismas versiones de herramientas y runtimes están disponibles en las tareas del agente
- Preinstalar dependencias del sistema (librerías nativas, compiladores, etc.)
- Configurar el entorno de compilación exacto que usa tu aplicación
- Reproducir condiciones específicas necesarias para correr pruebas.

---

### Relacionado

- [MCP en Sandbox →](./03_MCP.md)
- [Variables de entorno →](./02_Environment%20Variables.md)
- [Acceso a Internet →](./01_Internet%20Access.md)
- [Integración de GitHub →](../04_GitHub.md)

---

*📂 Capítulo: **GitHub***

## Integración de GitHub: agente autónomo

> **Fuente:** [kiro.dev/docs/autonomous-agent/github/](https://kiro.dev/docs/autonomous-agent/github/)

---

### Instalación

Conecta tu cuenta de GitHub al Agente Autónomo Kiro:

1. Navegá a [app.kiro.dev/agent](https://app.kiro.dev/agent) y ve a **Configuración**
2. Seleccione **"Connect GitHub"** bajo Integraciones
3. Autorizá la **aplicación Kiro Agent GitHub**
4. Otorgá acceso a repositorios específicos o todos los repositorios de tu organización

> La aplicación Kiro Agent GitHub solo necesita instalarse **una vez por organización o cuenta**. Los propietarios de la organización seleccionan a qué repositorios pueden acceder la aplicación, controlando qué repositorios están disponibles para Kiro.

**Visibilidad de repositorios por usuario:** Cada usuario ve todos los repositorios donde se cumplen ambas condiciones:
1. La aplicación Kiro Agent GitHub fue instalada y autorizada para ese repositorio
2. La cuenta de GitHub del usuario tiene acceso a ese repositorio

Los usuarios solo pueden asignar tareas a repositorios donde tienen **permisos de escritura**. Otros usuarios no pueden asignar tareas en tu nombre.

---

### Asignación de tareas desde problemas de GitHub

Podés asignar trabajo directamente desde issues de GitHub de dos maneras:

**Con la etiqueta `kiro`:**  
Kiro comenzará a trabajar en la tarea y escuchará todos los comentarios del número para contexto o feedback adicional.

**Con el comando `/kiro` en un comentario:**  
Asigna ese tema específico a Kiro.

Si usas `/kiro` pero no registras tu cuenta de GitHub en Kiro, recibirás instrucciones para hacerlo. La aplicación Kiro Agent GitHub debe estar instalada en el repositorio.

---

### Cómo funciona el agente con GitHub

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

### Abordar los comentarios de relaciones públicas

Kiro proporciona dos comandos para manejar comentarios de pull request:

| comando | Descripción |
|---|---|
| `/kiro todos` | Aborda todos los comentarios de todos los revisores en todo el PR. Ideal para manejar todo el feedback a la vez. |
| `/kiro arreglar` | Aborda todos los comentarios dentro de un hilo de conversación específico. Ideal para focalizarse en un tema a la vez. |

Para prevenir que un comentario sea abordado, elimínelo o respondé con su propia perspectiva antes de usar un comando.

También podés dar comentarios desde la vista de tareas en [app.kiro.dev/agent](https://app.kiro.dev/agent).

**Comentarios de acciones de GitHub** (verificaciones automatizadas, pruebas, análisis de seguridad) se aborda automáticamente cuando hay cualquier comentario.

#### Enseñar al agente mediante revisiones de código

Podés enseñarle al agente los patrones de tu equipo a través del feedback en PRs. Cuando dejás comentarios como "recordá usar nuestro manejo estándar de errores" o "siempre sigue nuestras convenciones de naming", el agente aprende y esos aplicaciones patrones en trabajos futuros en todos tus repositorios.

> Solo **tu feedback** influye en el aprendizaje del agente. Los comentarios de otros revisores no afectan lo que aprende.

---

### Múltiples usuarios en el mismo repositorio

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

### Permisos

#### Instalación y configuración de la aplicación

La aplicación Kiro Agent GitHub se instala una vez por organización o cuenta por un propietario. La configuración de la aplicación es global y define el conjunto máximo de repositorios a los que Kiro puede acceder.

#### Acceso a nivel de repositorio

Cada usuario solo puede trabajar con repositorios donde se cumplen ambas condiciones:
- La aplicación Kiro Agent GitHub tiene acceso otorgado por un propietario de la organización
- El usuario tiene permisos de escritura en el repositorio

#### Se requieren permisos de repositorio

**Leer y escribir:**
- Acciones: flujos de trabajo, ejecuciones de flujos de trabajo y artefactos
- Cheques — Cheques sobre el código
- Contenidos — Contenidos del repositorio, commits, Branches, Releases y merges
- Issues — Issues y comentarios relacionados, asignados, etiquetas e hitos
- Pull requests: relaciones públicas y comentarios relacionados, asignados, etiquetas, hitos y fusiones
- Flujos de trabajo — Actualizar archivos de flujo de trabajo de GitHub Action

**Solo lectura:**
- Metadatos — Buscar repositorios, listar colaboradores (obligatorio)
- Administración — Configuración del repositorio, equipos y colaboradores
- Confirmar estados

**Permisos de organización (solo lectura):**
- Administración — Gestionar acceso a la organización

#### Eventos de webhook

La aplicación se suscribe a: pull requests, revisiones de pull requests, comentarios de revisión de pull requests, problemas, comentarios de problemas, eventos de inserción, creación/eliminación de ramas/etiquetas, lanzamientos, cambios en el repositorio, ejecuciones de flujo de trabajo, y otros.

#### Revocación

- **Propietarios de la organización** pueden revocar el acceso del agente en cualquier momento removiendo permisos de repositorios de la aplicación Kiro Agent GitHub (bloquea el acceso para todos los usuarios)
- **Usuarios individuales** pueden desconectar su cuenta de GitHub de Kiro en cualquier momento, lo que detiene su agente de acceso a cualquier repositorio

#### Protección de sucursales

El agente respeta tus reglas de protección de sucursal. No puedes pushear directamente a sucursales protegidas y debes pasar por tu flujo de trabajo estándar de pull request.

---

### Relacionado

- [Configuración →](../01_Get%20started/01_Setup.md)
- [Creando tareas →](../02_Using%20the%20agent/02_Creating%20tasks.md)
- [Protección de datos →](./05_Data%20protection.md)

---

*📂 Capítulo: **Data protection***

## Protección de datos — Agente autónomo

> **Fuente:** [kiro.dev/docs/autonomous-agent/data-protection/](https://kiro.dev/docs/autonomous-agent/data-protection/)

---

### Modelo de responsabilidad compartida

El [Shared Responsibility Model de AWS](https://aws.amazon.com/compliance/shared-responsibility-model/) aplica a la protección de datos en el Agente Autónomo Kiro:

| AWS es responsable de | Vos sos responsable de |
|---|---|
| Proteger la infraestructura global de la nube de AWS | Mantener control sobre tu contenido en esa infraestructura |
| Seguridad física de centros de datos | Configuración de seguridad y tareas de gestión de los servicios AWS que usamos |

Para obtener más información, consulte [Preguntas frecuentes sobre privacidad de datos →](https://aws.amazon.com/compliance/data-privacy-faq/).

---

### Almacenamiento de datos

El Agente Autónomo El Kiro almacena:
- Descripciones de tareas
- Mensajes de chat
- Cambios de código
- Contexto adicional

Esta información se usa para ejecutar tareas y generar respuestas.

#### Regiones de AWS donde se almacena el contenido

> **Durante el Preview:** Todo el contenido del Kiro Autónomo Agente (descripciones de tareas, mensajes de chat, cambios de código) se almacena en la región **US East (N. Virginia)**.

Con inferencia entre regiones, tu contenido puede procesarse en una región diferente dentro de los Estados Unidos.

---

### Procesamiento entre regiones

Para mejorar la disponibilidad y el rendimiento, Kiro puede procesar solicitudes usando infraestructura en múltiples regiones de AWS dentro de los Estados Unidos.

** Regiones soportadas para inferencia entre regiones del Agente Autónomo: **  
Este de EE.UU. (N. Virginia), Este de EE.UU. (Ohio), Oeste de EE.UU. (Oregón) *(y otras regiones de EE.UU. según disponibilidad)*

---

### Cifrado de datos

#### Cifrado en tránsito

Toda la comunicación entre:
- Clientes y el Kiro Agente Autónomo
- El Kiro Agente Autónomo y sus dependencias aguas abajo

está usando conexiones protegidas **TLS 1.2 o superior**.

#### Cifrado en reposo

El Agente Autónomo de Kiro cifra tus datos usando **claves de cifrado propiedad de AWS** de AWS Key Management Service (AWS KMS). No necesitás tomar ninguna acción para proteger las claves administradas que cifran tus datos.

Ver [Claves propiedad de AWS →](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#aws-owned-cmk) para más información.

---

### Mejora del servicio

Para ayudar a Kiro a proporcionar la información más relevante, AWS puede usar cierto contenido del Kiro Autónomo Agente para **mejora del servicio**.

#### Contenido utilizado para mejorar el servicio

El contenido que Kiro puede usar incluye:
- Descripciones de tareas
- Mensajes de chat
- Otros insumos que proporcionalás
- Respuestas y código que genera Kiro

Este contenido puede usarse para: mejorar respuestas a preguntas comunes, corregir problemas operativos de Kiro, depuración o entrenamiento de modelos.

---

### Optar por no compartir datos

Por defecto, el Agente Autónomo Kiro recopila contenido para mejorar el servicio.

#### Cómo darse de baja

1. Vaya a [app.kiro.dev/agent/settings](https://app.kiro.dev/agent/settings)
2. Navegar a la sección **Recopilación de datos**
3. Desactivar **"Permitir que AWS utilice el contenido de su agente autónomo Kiro para mejorar el servicio"**

---

### Relacionado

- [Integración de GitHub →](./04_GitHub.md)
- [Agente Sandbox →](./03_Agent%20Sandbox/)
- [Política de privacidad de AWS →](https://aws.amazon.com/privacy/)