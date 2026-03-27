# Manual Consolidado: Kiro IDE

> Este documento es una consolidación extensa y detallada de toda la documentación referida a esta herramienta.



---

*📂 Capítulo: **Get started > Installation***

## Instalación

> **Fuente:** [kiro.dev/docs/getting-started/installation/](https://kiro.dev/docs/getting-started/installation/)
> **Página actualizada:** 9 de febrero de 2026

---

### Requisitos del sistema

Kiro está disponible para **macOS**, **Windows** y **Linux**.

- **macOS**: se ejecuta en procesadores Intel y Apple con las últimas actualizaciones de seguridad.
- **Windows**: compatible con Windows 10 y 11 (solo 64 bits). Actualmente, ARM no es compatible.
- **Linux**: requiere glibc 2.39 o superior. Por ejemplo: Ubuntu 24+, Debian 13+, Fedora 40+, Arch Linux y Linux Mint 22+.

---

### Descargar Kiro

Comenzar es simple:

1. Vaya a [kiro.dev](https://kiro.dev) y descargue el instalador.
2. Abra el archivo descargado y siga las instrucciones de instalación para su sistema operativo (Windows, macOS o Linux).
3. ¡Abre Kiro IDE y comienza a codificar!

---

### Primera ejecución

![Kiro_3](https://kiro.dev/videos/kiro_3.mp4)

1. Cuando abra Kiro por primera vez, se le pedirá que inicie sesión con un proveedor de su elección que incluya opciones sociales y de inicio de sesión de AWS. Obtenga más información sobre los [métodos de autenticación] (https://kiro.dev/docs/getting-started/authentication).

2. Una vez que haya iniciado sesión, puede elegir [importar su código VS](https://kiro.dev/docs/guides/migrating-from-vscode) configuraciones y extensiones. Si está utilizando otro editor, puede omitir este paso. Seleccione su tema preferido entre las opciones disponibles, luego permita que Kiro configure la integración del shell, permitiendo que el agente ejecute comandos en su nombre.

3. Finalmente, llegarás a la página de bienvenida. Abra un proyecto para comenzar y continuar con [su primer proyecto](https://kiro.dev/docs/getting-started/first-project).

---

### Soporte de idiomas

Kiro es compatible con los lenguajes de programación más populares. Contamos con guías que ayudan a configurar su entorno y mejores prácticas para los siguientes idiomas:

- [TypeScript y JavaScript](https://kiro.dev/docs/guides/languages-and-frameworks/typescript-javascript-guide)
- [Java](https://kiro.dev/docs/guides/languages-and-frameworks/java-guide)
- [Python](https://kiro.dev/docs/guides/languages-and-frameworks/python-guide)

---

### Próximos pasos

- [Métodos de autenticación →](https://kiro.dev/docs/getting-started/authentication/)
- [Tu primer proyecto →](https://kiro.dev/docs/getting-started/first-project/)

---

*📂 Capítulo: **Get started > Authentication***

## Métodos de autenticación

> **Fuente:** [kiro.dev/docs/getting-started/authentication/](https://kiro.dev/docs/getting-started/authentication/)
> **Página actualizada:** 19 de marzo de 2026

---

Kiro admite los siguientes proveedores de autenticación:

| Proveedor | Descripción |
|---|---|
| **GitHub** | Integración perfecta con su cuenta de GitHub |
| **Google** | Inicia sesión con tus credenciales de Google |
| **ID del creador de AWS** | Configuración rápida para desarrolladores individuales |
| **Centro de identidad de AWS IAM** | Autenticación de nivel empresarial |
| **Proveedor de identidad externo** | Conéctese a través del IdP de su organización (por ejemplo, Microsoft Entra ID u Okta) |

> **Información:** Los usuarios que tienen una suscripción paga de Kiro y acceden a ella a través de un proveedor de inicio de sesión social (como GitHub o Google) o mediante AWS Builder ID se consideran **suscriptores individuales**. Podemos utilizar cierto contenido de Kiro Free Tier y de suscriptores individuales de Kiro para mejorar el servicio. Para obtener más información sobre la mejora del servicio y cómo darse de baja, consulte [Mejora del servicio](https://kiro.dev/docs/privacy-and-security/).

Kiro es una aplicación de AWS que funciona como un IDE agente independiente **sin necesidad de configurar una cuenta de AWS**. Puede descargar y usar Kiro inmediatamente sin ninguna configuración de cuenta externa: maneja las interacciones de IA y la asistencia de código directamente a través de la propia aplicación.

---

### Métodos de autenticación disponibles

#### GitHub

Utilice las siguientes instrucciones para iniciar sesión en Kiro usando GitHub.

**Para iniciar sesión con GitHub:**

1. En Kiro, elija **Iniciar sesión con GitHub**. Serás redirigido a tu navegador web predeterminado para completar el proceso de inicio de sesión.
2. Ingrese su nombre de usuario o dirección de correo electrónico y su contraseña y luego elija **Iniciar sesión**.
3. Elija **Autorizar kirodotdev** para autorizar la aplicación Kiro con su cuenta de GitHub.

---

#### Google

Utilice las siguientes instrucciones para iniciar sesión en Kiro mediante Google.

**Para iniciar sesión con Google:**

1. En Kiro, elija **Iniciar sesión con Google**. Serás redirigido a tu navegador web predeterminado para completar el proceso de inicio de sesión.
2. Elige una cuenta de Google que quieras usar con Kiro.
3. Elija **Continuar** para autorizar la aplicación Kiro con su cuenta de Google.

---

#### ID del creador de AWS

Utilice las siguientes instrucciones para iniciar sesión en Kiro utilizando AWS Builder ID.

**Para iniciar sesión con AWS Builder ID:**

1. En Kiro, elija **Iniciar sesión con AWS Builder ID**. Serás redirigido a tu navegador web predeterminado para completar el proceso de inicio de sesión.
2. Ingrese su dirección de correo electrónico y luego elija **Siguiente**.
3. Ingrese su contraseña y luego elija **Iniciar sesión**.
4. Elija **Permitir acceso** para autorizar la aplicación Kiro.

---

#### Centro de identidad de AWS IAM

Utilice las siguientes instrucciones para iniciar sesión en Kiro en su organización, incluido AWS GovCloud (EE. UU.), mediante AWS IAM Identity Center.

**Para iniciar sesión con AWS IAM Identity Center:**

1. En Kiro, elija **Iniciar sesión con AWS IAM Identity Center**.
2. En **URL de inicio**, ingrese la URL de inicio proporcionada por su administrador o servicio de asistencia.
3. En **Región**, ingrese la región de AWS que aloja el directorio de identidad y luego elija **Continuar**.

> **Información:** Los métodos de autenticación admitidos en las regiones de AWS GovCloud (EE. UU.) son **AWS IAM Identity Center** y **proveedores de identidad externos**. Los métodos de inicio de sesión individuales, como GitHub, Google y AWS Builder ID **no están disponibles** en las regiones de AWS GovCloud (EE. UU.).
>
> Los usuarios saben que usarán Kiro con AWS GovCloud (EE. UU.) asegurándose de que la URL de inicio utilizada durante la autenticación contenga `"us-gov-home"`, por ejemplo:
> ```
> https://start.us-gov-home.awsapps.com/directory/d-XXXXXXXXXX
> ```
>
> Kiro utiliza la misma descarga/instalador para las regiones comerciales y AWS GovCloud (EE. UU.). La autenticación de IAM Identity Center enruta automáticamente el tráfico a la región adecuada de AWS GovCloud (EE. UU.). **Kiro IDE versión 0.9.2+** y **Kiro CLI versión 1.25.0+** son necesarios para la compatibilidad con las regiones de AWS GovCloud (EE. UU.).

---

#### Proveedor de identidad externo

Utilice las siguientes instrucciones para iniciar sesión en Kiro utilizando el proveedor de identidad externo de su organización, como Microsoft Entra ID u Okta.

**Para iniciar sesión con el proveedor de identidad de su organización:**

1. En Kiro, elige **Tu organización**.
2. Ingrese su correo electrónico de trabajo para encontrar su organización y luego elija **Continuar**.
3. Complete el proceso de inicio de sesión con el proveedor de identidad de su organización.

---

### Solución de problemas de autenticación

Si encuentra problemas durante el proceso de autenticación, como fallas de redireccionamiento del navegador o errores de inicio de sesión, consulte nuestra [guía de solución de problemas](https://kiro.dev/docs/troubleshooting/#authentication-issues) para obtener soluciones específicas de la plataforma y correcciones comunes.

---

### Próximos pasos

- [Revisar preguntas frecuentes →](https://kiro.dev/faq)
- [Explorar funciones del Agente →](https://kiro.dev/docs/chat)
- [Comenzar con Kiro →](https://kiro.dev/docs)

---

*📂 Capítulo: **Get started > Your first project***

## Tu primer proyecto

> **Fuente:** [kiro.dev/docs/getting-started/first-project/](https://kiro.dev/docs/getting-started/first-project/)

---

Esta guía lo guía a través de las características esenciales de Kiro trabajando con un proyecto real. Aprenderá a utilizar **archivos de Steering**, **especificaciones**, **hooks** y **servidores MCP** para mejorar su flujo de trabajo de desarrollo.

---

### Requisitos previos

Antes de comenzar, asegúrese de tener:

- [Kiro instalado](https://kiro.dev/docs/getting-started/installation)
- Un proyecto con el que trabajar (ya sea un proyecto existente o uno nuevo)
- Familiaridad básica con la estructura y la tecnología de su proyecto.

---

### Abre tu proyecto

1. **Inicia Kiro** y abre tu proyecto:
   - Utilice **Archivo > Abrir carpeta** para seleccionar el directorio de su proyecto
   - O arrastra y suelta la carpeta de tu proyecto en Kiro
   - O vaya a la línea de comando y ejecute `kiro.` desde el directorio de su proyecto

2. **Accede al Panel Kiro:**
   - Haz clic en el **icono de Kiro Ghost** en la barra de actividades (barra lateral izquierda)
   - Este panel proporciona acceso a todas las funciones impulsadas por la IA de Kiro.

3. **Iniciar una sesión de chat:**
   - El panel de chat debería estar abierto de forma predeterminada.
   - Esto abre la interfaz conversacional de Kiro donde puedes interactuar con la IA.

![Kiro Panel](https://kiro.dev/videos/kiro-pane.mp4)

---

### Configurar archivos de Steering

Los archivos de Steering brindan contexto sobre su proyecto, lo que ayuda a Kiro a comprender su código base, convenciones y requisitos.

Para comenzar, elija **Generar documentos de Steering** en el panel Kiro. Kiro genera documentos de Steering del proyecto almacenados en `.kiro/steering/` que guían el comportamiento de Kiro.

Contienen información sobre:

- Su producto y su propósito
- Pila técnica y marcos.
- Estructura y convenciones del proyecto.

También puede crear archivos de Steering personalizados haciendo clic en el botón **+** en la sección de dirección y agregar cosas como estándares de codificación, flujos de trabajo y mejores prácticas del equipo. [Más información sobre la dirección aquí →](https://kiro.dev/docs/steering/)

![Dirección Kiro](https://kiro.dev/videos/kiro-steering.mp4)

---

### Construir funciones con especificaciones

Las especificaciones transforman ideas de funciones de alto nivel en planes de implementación detallados a través de tres fases:

1. **Requisitos** — Historias de usuarios con criterios de aceptación en notación EARS
2. **Diseño**: arquitectura técnica y enfoque de implementación
3. **Tareas**: pasos de implementación discretos y rastreables

![Inicio de especificaciones](https://kiro.dev/videos/specs-start.mp4)

#### Crea tu primera especificación

1. **Iniciar una nueva especificación:**
   - En tu sesión de chat, haz clic en el botón **Especificación**
   - O elige el botón **+** en la sección Especificaciones del panel Kiro

2. **Ingrese una descripción de la función:**
   - Describe tu característica en lenguaje natural.
   - Ejemplo: *"Agregar un sistema de autenticación de usuario con funcionalidad de inicio de sesión, cierre de sesión y restablecimiento de contraseña"*

3. **Siga el flujo de trabajo guiado:**
   - **Fase de requisitos:** Kiro le ayudará a estructurar sus requisitos utilizando la notación EARS.
   - **Fase de diseño:** Se documentará la arquitectura técnica y el diseño de componentes.
   - **Fase de implementación:** Se generarán tareas discretas para su ejecución.

#### Ejecutar tareas específicas

![Tarea específica](https://kiro.dev/videos/spec-task.gif)

Una vez que su especificación esté completa:

1. Revise **Tareas generadas** en el archivo `tasks.md`
2. **Ejecutar tareas** haciendo clic en elementos de tareas individuales
3. **Seguimiento del progreso** a medida que las tareas se actualizan automáticamente a *"En curso"* y *"Listo"*

![Ejecutar tareas específicas](https://kiro.dev/videos/spec-task.gif)

---

### Automatizar flujos de trabajo con hooks

![Hooks](https://kiro.dev/videos/hooks.gif)

Agent Hooks elimina el trabajo manual al ejecutar automáticamente acciones predefinidas cuando:

- Los archivos se crean, guardan o eliminan
- Los disparadores manuales están activados.
- Se modifican patrones de archivos específicos.

**Para empezar:**

1. **Creación de gancho de acceso:**
   - Navega a la sección **Agent Hooks** en el panel de Kiro.
   - Haga clic en el botón **+** para crear un nuevo gancho.

2. **Definir comportamiento del gancho:**
   - Describe lo que quieres automatizar en lenguaje natural.
   - Ejemplo: *"Cuando guardo un archivo de componente de React, creo o actualizo automáticamente su archivo de prueba correspondiente"*

3. **Configurar ajustes de enlace:**
   - **Tipo de evento:** Elija cuándo se activa el enlace: eventos de archivos (creados, guardados, eliminados), eventos de ciclo de vida del agente y avisos (envío rápido, detención del agente, uso previo y posterior a la herramienta), eventos de tareas específicas (ejecución previa y posterior a la tarea) o activación manual
   - **Patrón de archivo:** Especifique qué archivos deben activar el enlace (por ejemplo, `src/**/*.tsx`)
   - **Instrucciones:** Definir las acciones específicas a realizar

![Automatizar flujos de trabajo con hooks](https://kiro.dev/videos/hooks.gif)

---

### Amplíe las capacidades con MCP

El Protocolo de contexto modelo (MCP) le permite a Kiro:

- Acceda a bases de conocimiento y documentación especializadas.
- Integrar con API y servicios externos
- Utilice herramientas y utilidades específicas del dominio.
- Conéctese a bases de datos y servicios en la nube.

#### Configurar MCP

1. Abra el panel de Kiro haciendo clic en el icono de Kiro Ghost en la barra de actividades. Primero habilite los MCP y luego haga clic en el botón de edición (icono de lápiz) junto a MCP en el panel.

2. De forma predeterminada, Kiro se envía con [buscar servidor MCP] (https://github.com/modelcontextprotocol/servers/tree/main/src/fetch) en el archivo JSON. Voltéelo a `disabled=false` para conectarse.

3. También puedes agregar cualquier servidor MCP pidiéndole a Kiro que agregue un nuevo servidor o editando el archivo JSON directamente:

```json
{
  "mcpServers": {
    "web-search": {
      "command": "uvx",
      "args": ["mcp-server-brave-search"],
      "env": {
        "BRAVE_API_KEY": "your-api-key-here"
      },
      "disabled": false,
      "autoApprove": ["search"]
    }
  }
}
```

#### Utilice herramientas MCP

Una vez configuradas, puede utilizar las herramientas MCP de varias maneras:

- **Preguntas directas**: haga preguntas que aprovechen las capacidades del servidor MCP:
  - Ejemplo: *"Buscar las últimas mejores prácticas de React 18"*

- **Uso explícito de herramientas**: haga referencia a herramientas MCP específicas con el proveedor de contexto `#MCP`:
  - Ejemplo: `#[fetch] fetch Utilice la búsqueda web para encontrar ejemplos de restricciones genéricas de TypeScript`

- **Integración con otras funciones**: combine MCP con hooks y especificaciones:
  - Ejemplo: *"Crear un enlace que utilice el MCP de búsqueda web para encontrar documentación relevante cuando creo nuevos archivos de componentes"*

---

### Próximos pasos

- [Pruebe el tutorial interactivo →](https://kiro.dev/docs/guides/learn-by-playing)
- [Más información sobre especificaciones →](https://kiro.dev/docs/specs)
- [Únete a la comunidad en Discord →](https://discord.gg/kirodotdev)

---

*📂 Capítulo: **Models***

## Modelos

> **Fuente:** [kiro.dev/docs/models/](https://kiro.dev/docs/models/)

---

Kiro admite múltiples modelos de IA. Puede cambiar de modelo desde el menú desplegable de la interfaz de chat; su selección se aplica a todos los mensajes posteriores de la conversación.

---

### Comparación rápida

El costo es relativo a **Automático (1,0 veces el valor de referencia)**. Por ejemplo, una tarea que cuesta 10 créditos en Auto costaría 22 créditos en Opus, 4 créditos en Haiku o 0,5 créditos en Qwen3 Coder Next.

| Modelo | Mejor para | Multiplicador de costos |
|---|---|---|
| **Automático** *(recomendado)* | Uso general, mejor relación calidad/coste | 1,0x |
| **Claude Opus 4.6** | Codificación agente compleja, depuración, grandes bases de código | ~2,2x |
| **Claude Opus 4.5** | Razonamiento avanzado, desafíos sofisticados | ~2,2x |
| **Claude Soneto 4.6** | Flujos de trabajo de desarrollo iterativos, canalizaciones multimodelo | ~1,0x |
| **Claude Soneto 4.5** | Agentes complejos, funcionamiento autónomo ampliado | ~1,0x |
| **Claude Soneto 4.0** | Selección de modelo consistente y predecible | ~1,0x |
| **Claude Haiku 4.5** | Iteraciones rápidas, correcciones simples, ahorro de crédito | ~0,4x |
| **MiniMax M2.5** | Ciclo de vida completo del desarrollo, revisión del código | 0,25x |
| **DeepSeek 3.2** | Flujos de trabajo agentes, generación de código | 0,25x |
| **MiniMax M2.1** | Programación multilingüe, generación de UI | 0,15x |
| **Qwen3 Coder Siguiente** | — | 0,5x |

---

### Detalles del modelo

#### Automático *(recomendado)*

El enrutador modelo de Kiro. Auto combina múltiples modelos de frontera con técnicas de optimización para ofrecer la mejor relación calidad-costo. Elige automáticamente el modelo óptimo para cada tarea y ofrece resultados de clase Sonnet 4. Auto utiliza los mejores modelos LLM de su clase (Claude Sonnet 4 y similares) y mantiene un nivel de alta calidad para garantizar que los resultados se comparen o superen los modelos individuales disponibles para usted.

---

#### Claude Opus 4.6

El modelo más capaz de Anthropic con codificación de última generación y rendimiento agente. Puntuaciones máximas en Terminal-Bench 2.0 y SWE-bench Verified para codificación agente. Se mantiene productivo durante sesiones más largas sin cambios de contexto y maneja bases de código de varios millones de líneas, planificando por adelantado y adaptándose según sea necesario. Las capacidades mejoradas de depuración y revisión de código le permiten detectar sus propios errores y pensar con más cuidado en problemas complejos, revisando el razonamiento antes de comprometerse. [Más información →](https://www.anthropic.com/research/claude-opus-4-6)

---

#### Claude Opus 4.5

El modelo más inteligente de Anthropic, que combina la máxima capacidad con un rendimiento práctico. Mejoras significativas en razonamiento, codificación y resolución de problemas a un precio más accesible que los modelos Opus anteriores. Maneja bien las compensaciones y la ambigüedad en múltiples sistemas, lo que lo hace adecuado para los desafíos de desarrollo de software más sofisticados. [Más información →](https://www.anthropic.com/news/claude-opus-4-5)

---

#### Claude Soneto 4.6

Una actualización completa de Sonnet 4.5 que se acerca a la inteligencia de Opus 4.6 y al mismo tiempo es más eficiente en términos de token. Destaca en flujos de trabajo de desarrollo iterativos y mantiene el contexto durante sesiones largas. Maneja funciones de agente principal y subagente en procesos multimodelo, lo que lo hace ideal para equipos que utilizan poderes de Kiro y subagentes personalizados. [Más información →](https://www.anthropic.com/news/claude-sonnet-4-6)

---

#### Claude Soneto 4.5

El mejor modelo de Anthropic para codificación y agentes complejos, con la mayor inteligencia en la mayoría de las tareas. Lo último en tecnología SWE-bench Verificado con operación autónoma extendida durante horas con uso efectivo de herramientas. Mejora de la planificación, el diseño de sistemas y la ingeniería de seguridad. [Más información →](https://www.anthropic.com/news/claude-sonnet-4-5)

---

#### Claude Soneto 4.0

Acceso directo a Claude Sonnet 4.0 de Anthropic para usuarios que prefieren una selección de modelos consistente. Mismo modelo para todas las interacciones sin capas de enrutamiento ni optimización. Control total y transparencia total, con comportamiento predecible para flujos de trabajo que dependen de características específicas del modelo. [Más información →](https://www.anthropic.com/news/claude-4)

---

#### Claude Haiku 4.5

El modelo más rápido de Anthropic con un rendimiento cercano a la frontera. Iguala el rendimiento de Sonnet 4 en razonamiento y codificación a más del doble de velocidad. Inteligencia cercana a la frontera a un costo de un tercio y el primer modelo Haiku con capacidades de pensamiento ampliadas. [Más información →](https://www.anthropic.com/news/claude-haiku-4-5)

---

#### MiniMax M2.5

Modelo de peso abierto que iguala el rendimiento de codificación de primera clase a una fracción del costo. Capacitado con aprendizaje reforzado en cientos de miles de entornos del mundo real, brindando resultados sólidos en todo el ciclo de vida de desarrollo, desde el diseño del sistema hasta la revisión del código. **Multiplicador de crédito de 0,25x** con inferencia ejecutándose en el este de EE. UU. (Norte de Virginia). [Más información →](https://www.minimax.io/news/minimax-m25)

---

#### Búsqueda profunda 3.2

Modelo de peso abierto más adecuado para flujos de trabajo agentes y generación de código. Maneja bien largas cadenas de llamadas de herramientas, sesiones con estado y razonamiento de varios pasos. **Multiplicador de crédito de 0,25x** con inferencia ejecutándose en el este de EE. UU. (Norte de Virginia). [Más información →](https://api-docs.deepseek.com/news/news250325)

---

#### MiniMax M2.1

Modelo de peso abierto más adecuado para programación multilingüe y generación de UI. Ofrece resultados sólidos en Rust, Go, C++, Kotlin, TypeScript y otros. **Multiplicador de crédito de 0,15 veces** con inferencia en el este de EE. UU. (Norte de Virginia) y la UE (Frankfurt). [Más información →](https://minimax.io/news/minimax-m21)

---

### Cómo los modelos se comportan de manera diferente

No todos los modelos funcionan de la misma manera. Comprender estas diferencias le ayudará a elegir la correcta:

| Dimensión | Obra | Soneto | haikus |
|---|---|---|---|
| **Profundidad de planificación** | Piensa más, considera casos extremos, revisa el razonamiento | Más directo, empieza a funcionar antes | Planificación inicial más rápida y mínima |
| **Autocorrección** | Opus 4.6 detecta sus propios errores durante su revisión | Estándar | Estándar |
| **Resistencia de la sesión** | Mantiene el enfoque durante largas sesiones de varios archivos | Bueno para sesiones medias | Lo mejor para interacciones breves y enfocadas |
| **Nivel de iniciativa** | Toma más iniciativa, cambios más amplios | Conservador, se atiene a lo pedido | Conservador |

---

### Ciclo de vida del modelo

Los modelos en Kiro pasan por dos etapas. Cada etapa refleja la madurez del modelo y el nivel de soporte que puede esperar.

> **Nota:** Las solicitudes de inferencia para **modelos experimentales** se pueden procesar en varias regiones de AWS a nivel mundial para optimizar la disponibilidad y el rendimiento. Consulte [protección de datos](https://kiro.dev/docs/privacy-and-security/data-protection/#global-cross-region-inference-for-experimental-features) para obtener detalles sobre la inferencia entre regiones.

---

### Mejores prácticas

- **Comience con Auto** para la mayoría del trabajo. Optimiza tanto la calidad como el coste de forma automática.
- **Cambie a Opus** cuando se encuentre con un problema complejo o necesite un trabajo continuo con varios archivos.
- **Utilice Haiku** para iteraciones rápidas, correcciones simples o cuando desee conservar créditos.
- **Supervise su uso** en la [configuración de su cuenta](https://kiro.dev/docs/billing/) para comprender cómo la elección del modelo afecta el consumo.
- **Incluye el costo del modelo en tu nivel:** Si usas principalmente Opus, considera Pro+ o Power para obtener más créditos. Consulte [planes y facturación](https://kiro.dev/docs/billing/) para obtener más detalles.

---

*📂 Capítulo: **Editor > Interface***

## Interfaz

> **Fuente:** [kiro.dev/docs/editor/interface/](https://kiro.dev/docs/editor/interface/)

---

### Componentes de la interfaz principal

![Interfaz Kiro](https://kiro.dev/images/kiro-interface.png)

#### Editor

El espacio de trabajo central donde escribes y editas código. Las características incluyen:

- Resaltado de sintaxis para múltiples idiomas.
- Números de línea e indicadores de error.
- Plegado de código para una mejor organización
- Múltiples pestañas para trabajar entre archivos
- Soporte de vista dividida para edición en paralelo

---

#### Panel de chat

Puedes utilizar el panel de chat para:

- Haga preguntas sobre su código
- Solicitar generación o modificaciones de código.
- Obtenga ayuda con la depuración y la resolución de problemas
- Solicite revisiones de código y sugerencias de optimización.
- Incluir contexto con comandos `#` (por ejemplo, `#Archivo`, `#Carpeta`)
- Generar código repetitivo y plantillas.

> **Consejo:** Para mover el panel de chat al lado opuesto del IDE, vaya a **Ver > Apariencia > Mover la barra lateral principal a la derecha** en la barra de menú superior.

---

#### Vistas

La barra lateral contiene varias vistas especializadas:

| Ver | Descripción |
|---|---|
| **Explorador** | Navegue por la estructura de archivos de su proyecto, consulte los indicadores de estado de Git y acceda a secciones especiales para especificaciones y servidores MCP |
| **Buscar** | Realice operaciones globales de búsqueda y reemplazo en todo su proyecto |
| **Control de fuente** | Administre operaciones de Git, vea cambios y maneje commits con [mensajes de commit generados por IA](https://kiro.dev/docs/editor/source-control) |
| **Ejecutar y depurar** | Ver variables, pilas de llamadas y gestionar puntos de interrupción durante las sesiones de depuración |
| **Extensiones** | Instalar y administrar extensiones IDE |
| **Kiro** | Una vista dedicada a funciones específicas de IA: administración de especificaciones, enlaces de agentes, dirección de agentes y servidores MCP |

---

#### Barra de estado

Ubicada en la parte inferior de la interfaz, la barra de estado proporciona:

- Información del archivo actual
- Rama de Git y estado de sincronización
- Recuentos de errores y advertencias.
- Indicadores de estado del agente.

---

#### Paleta de comandos

Accede rápidamente a los comandos de Kiro pulsando:
- **macOS:** `Cmd+Mayús+P`
- **Windows/Linux:** `Ctrl+Mayús+P`

Utilice la paleta de comandos para:
- Ejecutar acciones comunes
- Acceder a herramientas MCP
- Configurar ajustes
- Ejecutar hooks de agente

---

### Consejos de navegación

- Utilice [atajos de teclado](https://kiro.dev/docs/editor/keyboard-shortcuts/) para una navegación más rápida
- Aproveche la paleta de comandos para acceder rápidamente a las funciones
- Anclar archivos de uso frecuente para facilitar el acceso
- Utilice vistas divididas para comparar o hacer referencia al código
- Configurar los ajustes del espacio de trabajo para una experiencia personalizada

---

### Próximos pasos

- [Atajos de teclado →](https://kiro.dev/docs/editor/keyboard-shortcuts/)

---

*📂 Capítulo: **Editor > Keyboard shortcuts***

## Atajos de teclado

> **Fuente:** [kiro.dev/docs/editor/keyboard-shortcuts/](https://kiro.dev/docs/editor/keyboard-shortcuts/)

---

### General

| Acción | MacOS | Ventanas/Linux |
|---|---|---|
| Paleta de comandos | `Cmd+Mayús+P` | `Ctrl+Mayús+P` |
| Atajos de teclado | `Cmd+K Cmd+S` | `Ctrl+K Ctrl+S` |
| Terminal de alternancia | `Ctrl+\`` | `Ctrl+\`` |
| Nuevo archivo | `Cmd+N` | `Ctrl+N` |
| Cerrar archivo | `Cmd+W` | `Ctrl+W` |
| Guardar | `Cmd+S` | `Ctrl+S` |
| Guardar todo | `Cmd+Mayús+S` | `Ctrl+Mayús+S` |
| Deshacer | `Cmd+Z` | `Ctrl+Z` |
| Rehacer | `Cmd+Mayús+Z` | `Ctrl+Mayús+Z` |

---

### Navegación

| Acción | MacOS | Ventanas/Linux |
|---|---|---|
| Archivo de apertura rápida | `Cmd+P` | `Ctrl+P` |
| Abrir archivo | `Cmd+O` | `Ctrl+O` |
| Abrir carpeta | `Cmd+K Cmd+O` | `Ctrl+K Ctrl+O` |
| Ir a Símbolo | `Cmd+Mayús+O` | `Ctrl+Mayús+O` |
| Ir a Línea | `Ctrl+G` | `Ctrl+G` |
| Buscar en Archivo | `Cmd+F` | `Ctrl+F` |
| Buscar en el espacio de trabajo | `Cmd+Mayús+F` | `Ctrl+Mayús+F` |
| Alternar barra lateral | `Cmd+B` | `Ctrl+B` |
| Editor dividido | `Cmd+\` | `Ctrl+\` |
| Grupo de editores de enfoque | `Cmd+1/2/3` | `Ctrl+1/2/3` |
| Control de fuente | `Ctrl+Mayús+G` | `Ctrl+Mayús+G` |

---

### Edición

| Acción | MacOS | Ventanas/Linux |
|---|---|---|
| Línea de corte | `Cmd+X` | `Ctrl+X` |
| Copiar línea | `Cmd+C` | `Ctrl+C` |
| Pegar | `Cmd+V` | `Ctrl+V` |
| Alternar comentario | `Cmd+/` | `Ctrl+/` |
| Mover línea arriba/abajo | `Opción+Arriba/Abajo` | `Alt+Arriba/Abajo` |
| Eliminar línea | `Cmd+Mayús+K` | `Ctrl+Mayús+K` |

---

### Funciones de IA

| Acción | MacOS | Ventanas/Linux |
|---|---|---|
| Abrir chat de IA | `Cmd+L` | `Ctrl+L` |
| Edición de IA en línea | `Cmd+I` | `Ctrl+I` |
| Ejecutar/depurar | `F5` | `F5` |

---

### Atajos personalizados

Puedes personalizar los atajos de teclado en Kiro:

1. Abra la paleta de comandos (`Cmd+Shift+P` / `Ctrl+Shift+P`)
2. Busque **Atajos de teclado**
3. Seleccione **Preferencias: Abrir atajos de teclado**
4. Seleccione el comando que desea modificar.
5. Elija el **ícono de lápiz** e ingrese su acceso directo preferido

Esto le permite crear un flujo de trabajo personalizado que coincida con sus preferencias y hábitos de otros editores.

---

*📂 Capítulo: **Editor > Codebase indexing***

## Indexación de base de código

> **Fuente:** [kiro.dev/docs/editor/codebase-indexing/](https://kiro.dev/docs/editor/codebase-indexing/)

---

Kiro indexa su código base para brindar asistencia de código inteligente y contextual. Comprender cómo funciona la indexación le ayudará a aprovechar al máximo las funciones de IA de Kiro.

---

### Cuando se produce la indexación

#### Indexación automática

Kiro realiza la indexación automáticamente en estos escenarios:

1. **Importación de proyectos**: cuando abres un proyecto por primera vez en Kiro, automáticamente comienza a indexar todos los archivos en tu espacio de trabajo.
2. **Cambios de archivos**: cuando se crean o agregan nuevos archivos a su proyecto, se indexan automáticamente.
3. **Cambios externos**: cuando los archivos se modifican fuera de Kiro (por ejemplo, mediante operaciones de git), se vuelven a indexar.

#### Indexación manual

Puede activar la indexación manualmente cuando sea necesario usando la **Paleta de comandos**:
- macOS: `Cmd+Mayús+P`
- Windows/Linux: `Ctrl+Mayús+P`

---

### Comandos de indexación disponibles

![Indexación de Kiro](https://kiro.dev/images/kiro-indexing.png)

#### Indexación de base de código

| Comando | Cuándo utilizar |
|---|---|
| `Kiro: Reindexación de la fuerza del código base` | Fuerza una reindexación completa de todo el código base. Utilícelo cuando: el índice parezca corrupto o incompleto, se hayan realizado cambios estructurales importantes o las sugerencias parezcan obsoletas. |
| `Kiro: Reconstruir el índice base del código` | Reconstruye completamente el índice de la base de código desde cero. Más completo que forzar la reindexación. Utilícelo cuando el índice parezca muy dañado o experimente problemas persistentes. |

#### Indexación de documentación

| Comando | Descripción |
|---|---|
| `Kiro: Índice de documentos` | Inicia la indexación de archivos de documentación en su proyecto |
| `Kiro: Docs fuerza la reindexación` | Fuerza una reindexación completa de todos los archivos de documentación |

---

### Monitoreo del progreso de la indexación

![Registros de indexación de Kiro](https://kiro.dev/images/kiro-indexing-logs.png)

Puedes monitorear el proceso de indexación a través del panel **Kiro Logs**:

1. Accede al panel **Salida** en Kiro
2. Seleccione **"Kiro Logs"** en el menú desplegable.
3. Vea el progreso de la indexación y las actualizaciones de estado en tiempo real.

Los registros muestran:
- Cuando comienza y finaliza la indexación.
- Número de archivos encontrados y procesados.
- Porcentaje de progreso para grandes bases de código
- Tiempo de finalización de las operaciones de indexación.

---

### Contenido indexado

Kiro indexa varios tipos de contenido para brindar asistencia inteligente:

| Tipo de contenido | Ejemplos |
|---|---|
| **Código fuente** | Todos los archivos de lenguajes de programación en su espacio de trabajo |
| **Documentación** | Markdown, MDX y otros formatos de documentación |
| **Configuración** | Archivos de configuración del proyecto y manifiestos |
| **Dependencias** | Definiciones de paquetes e información de dependencia |

Los datos indexados permiten funciones como:
- Finalización de código inteligente
- Navegación entre archivos
- Sugerencias contextuales
- Búsqueda de documentación.
- Asistencia de refactorización de código

---

*📂 Capítulo: **Editor > Source control***

## Control de fuente

> **Fuente:** [kiro.dev/docs/editor/source-control/](https://kiro.dev/docs/editor/source-control/)

---

Kiro mejora su flujo de trabajo de Git con la generación de mensajes de commit impulsada por IA y una perfecta integración del control de versiones.

---

### Confirmar generación de mensajes

![Mensaje de commit de Git](https://kiro.dev/videos/git-commit-message.mp4)

Kiro puede generar automáticamente mensajes de commit descriptivos siguiendo el formato [Commits convencionales](https://www.conventionalcommits.org/en/v1.0.0/) analizando sus cambios por etapas.

#### Cómo generar mensajes de commit

1. **Prepara tus cambios** en el panel de control de código fuente
2. Haga clic en el botón **🪄** junto al campo de entrada del mensaje de commit.
3. **Revise el mensaje generado**: Kiro analiza sus cambios y crea un mensaje de commit descriptivo.
4. **Edite si es necesario**: puede modificar el mensaje generado antes de confirmarlo.
5. **Confirma tus cambios** usando el mensaje generado o editado

> **Consejo:** Puedes configurar un atajo de teclado personalizado para `Kiro: Generar mensaje de commit` en la configuración de tu teclado para un acceso más rápido.

---

#### Formato del mensaje

Kiro sigue el formato de **Compromisos Convencionales**:

```
<type>(<scope>): <subject>
- First change or addition
- Second change or improvement
- Third change if applicable
- Why this change was needed (if relevant)
```

#### Tipos de compromiso convencionales

| Tipo | Descripción |
|---|---|
| `hazaña` | Nuevas características |
| `arreglar` | Corrección de errores |
| `docs` | Cambios en la documentación |
| `estilo` | Cambios de formato |
| `refactor` | Reestructuración del código |
| `prueba` | Agregar/actualizar pruebas |
| `tarea` | Tareas de mantenimiento |
| `perfeccionamiento` | Mejoras de rendimiento |
| `ci` | Cambios CI/CD |

#### Ejemplo

```
feat(docs): add comprehensive Source Control documentation
- Create new documentation page for Source Control features
- Update interface documentation to link to Source Control page
- Provide detailed explanation of AI-powered commit message generation
- Describe diff context provider and commit message generation process
```

---

### Proveedor de contexto Git Diff

Kiro incluye un proveedor de contexto `#Git Diff` que le permite hacer referencia a sus cambios actuales no confirmados directamente en el chat. Esto es útil para:

- Solucionar conflictos de fusión
- Revisar los cambios antes de comprometerlos.
- Obtener una revisión del código de tu diferencia actual

#### Ejemplo de uso

```
Hey Kiro, can you fix the merge conflicts? #Git Diff
```

---

### Solución de problemas

#### Error en las operaciones de Git

- Verifique su configuración y credenciales de Git
- Asegúrese de tener los permisos adecuados para el repositorio.

---

*📂 Capítulo: **Editor > Multi-root workspaces***

## Espacios de trabajo multiraíz

> **Fuente:** [kiro.dev/docs/editor/multi-root-workspaces/](https://kiro.dev/docs/editor/multi-root-workspaces/)

---

Los espacios de trabajo de múltiples raíces le permiten trabajar con múltiples carpetas de proyectos simultáneamente en una sola ventana de Kiro. Las funciones de IA de Kiro están diseñadas para funcionar sin problemas en todas las carpetas raíz.

---

### Funcionalidad principal

Kiro resolverá las rutas de los archivos de forma inteligente en todas las carpetas raíz mientras navega y actualiza su espacio de trabajo de múltiples raíces.

**[Codebase Indexing](https://kiro.dev/docs/editor/codebase-indexing/)** y Repository Maps funcionan perfectamente en espacios de trabajo de múltiples raíces: ambos índices contienen código de todas las carpetas raíz y se puede hacer referencia a ellos en las indicaciones exactamente como en escenarios de espacios de trabajo de una sola raíz.

Al agregar un archivo usando el proveedor de contexto `#file`, si hay varios archivos con el mismo nombre en diferentes carpetas raíz, Kiro mostrará una lista de archivos coincidentes con sus rutas para que pueda seleccionar el correcto.

---

### Especificaciones

Kiro recupera todos los archivos [spec](https://kiro.dev/docs/specs/) de la subcarpeta `.kiro` en **cada** de las carpetas raíz y los muestra como una lista unificada en la sección Especificaciones del panel Kiro. El nombre de la carpeta raíz que contiene se muestra junto a cada especificación.

- Puedes pedirle a Kiro que trabaje en una especificación definida en cualquiera de las carpetas raíz.
- Al crear una nueva especificación, Kiro determinará la carpeta raíz adecuada para colocarla.

---

### Archivos de Steering

Kiro recupera todos los archivos [dirección](https://kiro.dev/docs/steering/) de la subcarpeta `.kiro` debajo de cada carpeta raíz, mostrándolos como una lista unificada en la sección **Dirección del agente** del panel de Kiro bajo el grupo *Espacio de trabajo*. El nombre de la carpeta raíz se muestra junto a cada archivo de Steering del espacio de trabajo.

| Directiva | Comportamiento |
|---|---|
| **Siempre incluido** | Los archivos de Steering siempre se cargan, independientemente de en qué carpeta raíz esté trabajando el agente |
| **Inclusión condicional** | Se carga solo si el agente está trabajando en un archivo en esa misma raíz y el archivo coincide con el patrón de inclusión |

Al crear un nuevo archivo de Steering del espacio de trabajo, se le pedirá que elija la carpeta raíz para guardarlo.

---

### Hooks

Kiro recupera todos los [hooks](https://kiro.dev/docs/hooks/) de la subcarpeta `.kiro` debajo de cada carpeta raíz, mostrándolos como una lista unificada en la sección **Agent Hooks**. El nombre de la carpeta raíz se muestra al lado de cada enlace.

> **Importante:** Los enlaces Crear archivo, Guardar archivo y Eliminar archivo se activan **solo** cuando el agente modifica archivos ubicados en la misma carpeta raíz donde se define el enlace.

Al crear un nuevo enlace, se le pedirá que elija la carpeta raíz.

---

### Servidores MCP

Kiro recupera todas las definiciones de [servidor MCP](https://kiro.dev/docs/mcp/) de la subcarpeta `.kiro` debajo de cada carpeta raíz, mostrándolas como una lista unificada en la sección **Servidores MCP**.

- Todos los servidores MCP definidos en todas las raíces se inicializan al inicio.
- Si dos carpetas raíz definen un servidor MCP con el mismo nombre, se utiliza la definición en la **última raíz de definición**.
- Los servidores se inician con la **primera carpeta raíz** como directorio de trabajo actual.

> Cuando hace clic en **Abrir configuración de MCP**, verá la configuración de MCP a nivel de usuario (global) de forma predeterminada. Haga clic en **Configuración del espacio de trabajo** para ver la configuración a nivel del espacio de trabajo. En un espacio de trabajo con múltiples raíces, se le pedirá que elija la carpeta raíz.

---

*📂 Capítulo: **Editor > Kiroignore***

##kiroignorar

> **Fuente:** [kiro.dev/docs/editor/kiroignore/](https://kiro.dev/docs/editor/kiroignore/)

---

`.kiroignore` usa patrones de estilo gitignore para controlar a qué archivos puede acceder Kiro. Esto le brinda un control preciso sobre lo que el agente de IA puede leer e interactuar en su proyecto.

---

### ¿Por qué utilizar .kiroignore?

| Razón | Descripción |
|---|---|
| **Seguridad** | Evite que Kiro acceda a archivos que contengan credenciales, claves API u otros datos confidenciales |
| **Privacidad** | Excluir información confidencial de las interacciones de IA |
| **Cumplimiento** | Asegúrese de que Kiro no acceda a archivos que no deberían compartirse con servicios externos |
| **Enfoque** | Mantenga relevante el contexto de Kiro excluyendo archivos grandes o creando artefactos |

---

### Configurar el espacio de trabajo Ignorar

Para excluir archivos en un proyecto específico:

1. Cree un archivo `.kiroignore` en la raíz de su proyecto (o cualquier subdirectorio)
2. Agregue patrones para los archivos que desea excluir:

```
## Secretos y credenciales
.env
.env.*
!.env.ejemplo
*.pem
*.clave

## Directorios privados
secretos/
privado/
```

3. Abra **Configuración** (`Cmd+` en Mac o `Ctrl+` en Windows/Linux)
4. Busque **Archivos ignorados por el agente** (configuración: `kiroAgent.agentIgnoreFiles`)
5. Agregue `.kiroignore` a la matriz

Kiro ahora omitirá cualquier archivo que coincida con sus patrones.

> **Consejo:** Comience con las credenciales y los secretos: estos son los archivos de mayor prioridad a proteger. Siempre puedes ampliar tus patrones a medida que evoluciona tu proyecto.

---

#### Opciones de configuración

La configuración `kiroAgent.agentIgnoreFiles` acepta una variedad de nombres de archivos:

- Utilice varios tipos de archivos ignorados simultáneamente: `[".gitignore", ".kiroignore"]`
- Establezca en `[]` para deshabilitar los archivos ignorados a nivel del espacio de trabajo.

#### Subdirectorio Ignorar archivos

Al igual que `.gitignore`, puedes colocar archivos `.kiroignore` en subdirectorios para anular o extender patrones de los directorios principales. **Los patrones en el subdirectorio ignoran los archivos tienen prioridad** para los archivos dentro de ese subdirectorio.

---

### Archivos de ignorar globalmente

Kiro respeta automáticamente los archivos ignorados globales si existen; no se necesita configuración:

- `~/.kiro/settings/kiroignore` — Tus patrones globales de ignorancia de Kiro (se aplica a todos los proyectos)
- Archivo de ignoración global de Git (configurado a través de `core.excludesfile` en tu configuración de git): solo se aplica en repositorios de git

---

### Sintaxis del patrón

`.kiroignore` usa **sintaxis estándar de gitignore**:

| Patrón | Significado |
|---|---|
| `archivo.txt` | Ignorar un archivo específico |
| `*.log` | Ignore todos los archivos con extensión `.log` |
| `carpeta/` | Ignorar un directorio completo |
| `**/temp` | Ignore `temp` en cualquier directorio |
| `! mantener.txt` | Volver a incluir un archivo previamente ignorado |

> **Nota:** No puede volver a incluir un archivo si se excluye un directorio principal. Por ejemplo, si ignora `secrets/`, agregar `!secrets/public.txt` no funcionará. Utilice patrones más específicos en lugar de excluir todo el directorio.

---

### Ejemplos

#### Protección de claves y secretos API

```gitignorar
## Archivos de entorno con credenciales.
.env
.env.local
.env.producción

## Mantenga la plantilla accesible
!.env.ejemplo

## Archivos de certificado y clave
*.pem
*.clave
*.p12
credenciales/
```

#### Excluyendo artefactos de compilación y archivos de datos

```gitignorar
## Construir salidas
dist/
construir/
.siguiente/

## Archivos de datos
*.sql
*.volcado
datos/exportaciones/
```

#### Configuración de cumplimiento del equipo

```gitignorar
## Directorios de datos de clientes
datos-cliente/
pii/

## Documentos de auditoría y cumplimiento
cumplimiento/interno/
informes-de-auditoría/
```

> Utilice `.kiroignore` cuando necesite reglas diferentes para el acceso del agente frente al control de versiones, o para bloquear archivos que se rastrean en git pero que Kiro no debería leer.

---

### Mejores prácticas

- **Utilice comentarios** para documentar por qué se ignoran los archivos: útil para los miembros del equipo
- **Patrones de prueba** pidiéndole a Kiro que lea un archivo ignorado; indicará que el acceso está bloqueado
- **Revise los patrones periódicamente** a medida que evoluciona la estructura de su proyecto
- **Coordine con su equipo** patrones globales para lograr un comportamiento coherente en todos los espacios de trabajo.

---

*📂 Capítulo: **Editor > Extension registry***

## Registro de extensión personalizado

> **Fuente:** [kiro.dev/docs/editor/extension-registry/](https://kiro.dev/docs/editor/extension-registry/)

---

Kiro admite el uso de un registro de extensión personalizado en lugar del [Registro Open VSX] predeterminado (https://open-vsx.org). Esto es útil para organizaciones que albergan su propio mercado de extensión privado.

---

### Configurar un mercado de extensiones diferente

#### Paso 1: busque el archivo `product.json`

Busque el archivo en el disco. La ubicación exacta depende de la plataforma:

| Plataforma | Camino |
|---|---|
| **macOS** | `/Aplicaciones/Kiro.app/Contents/Resources/app/product.json` |
| **Windows** | `C:\Archivos de programa\Kiro\resources\app\product.json` |
| **Linux** | `/usr/lib/code/product.json` |

#### Paso 2: edite la propiedad `extensionsGallery`

Abra `product.json` en un editor y busque la propiedad `extensionsGallery`. Actualice `serviceUrl`, `itemUrl` y `resourceUrlTemplate` para que apunten a su registro privado en lugar de `https://open-vsx.org`.

#### Paso 3: aplicar la configuración

Por ejemplo, si su registro personalizado está alojado en `https://registry.example.com`, actualice la propiedad `extensionsGallery` de la siguiente manera:

```json
"extensionsGallery": {
    "serviceUrl": "https://registry.example.com/vscode/gallery",
    "itemUrl": "https://registry.example.com/vscode/item",
    "resourceUrlTemplate": "https://registry.example.com/vscode/unpkg/{publisher}/{name}/{version}/{path}",
    "controlUrl": "",
    "recommendationsUrl": "",
    "nlsBaseUrl": "",
    "publisherUrl": ""
}
```

---

### Implementación empresarial

Para configurar todas las instalaciones de Kiro en su organización para usar un registro de extensión personalizado, use una solución de administración de puntos finales, **Administración de dispositivos móviles (MDM)** o similar para realizar la actualización anterior a `product.json` en todos sus dispositivos.

---

*📂 Capítulo: **Specs > Feature Specs***

## Especificaciones

> **Fuente:** [kiro.dev/docs/specs/](https://kiro.dev/docs/specs/)

---

Las especificaciones o especificaciones son artefactos estructurados que formalizan el proceso de desarrollo de funciones y corrección de errores en su aplicación. Proporcionan un enfoque sistemático para transformar ideas de alto nivel en planes de implementación detallados con un seguimiento y una rendición de cuentas claros.

Con las especificaciones de Kiro, puedes:
- Dividir los requisitos en historias de usuarios con criterios de aceptación.
- Crear documentos de diseño con diagramas de secuencia y planos de arquitectura.
- Seguimiento del progreso de la implementación en tareas discretas
- Colaborar eficazmente entre los equipos de producto e ingeniería.

---

### Estructura central

Cada especificación genera tres archivos clave:

| Archivo | Propósito |
|---|---|
| `requisitos.md` (o `bugfix.md`) | Captura historias de usuarios, criterios de aceptación o análisis de errores en notación estructurada |
| `diseño.md` | Documenta la arquitectura técnica, los diagramas de secuencia y las consideraciones de implementación.
| `tareas.md` | Proporciona un plan de implementación detallado con tareas discretas y rastreables |

---

### Flujo de trabajo trifásico

Todas las especificaciones siguen un flujo de trabajo de tres fases:

**1. Requisitos o análisis de errores**: defina lo que se debe crear o corregir
- Especificaciones de funciones: historias de usuarios y criterios de aceptación en `requirements.md`
- Especificaciones de corrección de errores: análisis de errores con comportamiento actual/esperado/sin cambios en `bugfix.md`

**2. Diseño**: cree una arquitectura técnica y un enfoque de implementación en `design.md`
- Arquitectura del sistema y diseño de componentes.
- Diagramas de secuencia y flujo de datos.
- Manejo de errores y estrategia de prueba.

**3. Tareas**: genera tareas de implementación discretas y ejecutables en `tasks.md`
- Tareas rastreables con resultados claros
- Actualizaciones de estado en tiempo real a medida que implementas
- Ejecutar tareas individualmente o todas a la vez

---

### Ejecución de tareas

Kiro proporciona una interfaz de ejecución de tareas para archivos `tasks.md` que muestra actualizaciones de estado en tiempo real. Las tareas se actualizan como en progreso o completadas, lo que le permite realizar un seguimiento eficiente del progreso de la implementación.

---

### Tipos de especificaciones

| Tipo | Lo mejor para |
|---|---|
| **Especificaciones de funciones** | Nuevas características que requieren planificación estructurada y requisitos EARS |
| **Especificaciones de corrección de errores** | Corrección de errores con precisión quirúrgica y evitando regresiones |

---

### Empezando

1. Desde el panel Kiro, haga clic en el botón **+** debajo de Especificaciones. Alternativamente, elija **Especificación** en el panel de chat.
2. Kiro te preguntará si estás desarrollando una **Función** o solucionando un **Error**
   - Si elige **Función**, describa su función y elija su flujo de trabajo: Requisitos primero o Diseño primero
   - Si elige **Error**, describa su error.
3. Siga el flujo de trabajo en cada fase hasta la implementación.

---

### Cuándo utilizar Specs frente a Vibe

| Utilice especificaciones cuando... | Utilice Vibe cuando... |
|---|---|
| Construcción de características complejas que requieren una planificación estructurada | Codificación exploratoria rápida |
| Corrección de errores en los que las regresiones son costosas | Prototipos sin objetivos claros |
| Necesita documentación para la colaboración en equipo | |
| Requisitos o necesidad de diseño iteración | |

---

### Más información

- [Especificaciones de funciones →](https://kiro.dev/docs/specs/feature-specs/)
- [Especificaciones de corrección de errores →](https://kiro.dev/docs/specs/bugfix-specs/)
- [Mejores prácticas →](https://kiro.dev/docs/specs/best-practices/)

---

*📂 Capítulo: **Specs > Bugfix Specs***

## Especificaciones de corrección de errores

> **Fuente:** [kiro.dev/docs/specs/bugfix-specs/](https://kiro.dev/docs/specs/bugfix-specs/)

---

Bugfix Specs proporciona un enfoque estructurado para diagnosticar y corregir errores sistemáticamente con precisión quirúrgica y al mismo tiempo prevenir regresiones.

---

### Beneficios clave

| Beneficio | Descripción |
|---|---|
| **Correcciones quirúrgicas** | Las restricciones explícitas garantizan que sólo se realicen los cambios necesarios |
| **Prevención de regresión** | El comportamiento sin cambios está documentado y probado |
| **Documentación** | Registro completo del error, corrección y razonamiento para referencia futura |
| **Confiabilidad** | El flujo de trabajo estructurado evita los errores comunes de las correcciones ad hoc |

---

### Cuándo utilizar las especificaciones de corrección de errores

Lo mejor para:
- Errores complejos que requieren análisis de causa raíz
- Errores en rutas de código críticas donde las regresiones son costosas
- Errores que necesitan documentación para cumplimiento o conocimiento del equipo.
- Situaciones en las que intentos de reparación anteriores provocaron regresiones

---

### Cómo funciona

Las especificaciones de corrección de errores siguen el mismo flujo de trabajo de tres fases que las especificaciones de funciones (Requisitos → Diseño → Tareas), pero con contenido diseñado para correcciones de errores quirúrgicos:

#### 1. Fase de análisis de corrección de errores

En lugar de un documento de requisitos, crea un `bugfix.md` que captura:

```
Comportamiento actual (defecto)
- CUANDO [condición] ENTONCES el sistema [comportamiento incorrecto]

Comportamiento esperado (correcto)
- CUANDO [condición] ENTONCES el sistema DEBE [comportamiento correcto]

Comportamiento sin cambios (prevención de regresión)
- CUANDO [condición] ENTONCES el sistema CONTINUARÁ CON [comportamiento existente]
```

Esta estructura explícita garantiza que Kiro comprenda no sólo lo que está roto, sino también lo que debe seguir funcionando.

#### 2. Fase de diseño

Kiro explora el código base para encontrar la causa raíz del problema y genera un `design.md` con:
- Análisis de causa raíz
- Enfoque de solución propuesto
- Propiedades a probar:
  - La implementación actual produce un comportamiento incorrecto *(valida la existencia del error)*
  - La implementación fija produce un comportamiento correcto *(valida que la solución funciona)*
  - La implementación sin cambios continúa funcionando *(evita regresiones)*

#### 3. Fase de Tareas

Las tareas de implementación se generan con [pruebas basadas en propiedades (PBT)](https://kiro.dev/docs/specs/correctness) que validan:
- El error es reproducible.
- El error está arreglado.
- No se introducen regresiones.

---

### Empezando

1. Elija **Especificación** en el panel de chat.
2. Describe el error, incluyendo:
   - Cuando ocurre el error (pasos de reproducción)
   - ¿Qué debería pasar en su lugar?
   - Cualquier restricción (código que no debe modificarse)
3. Elige **Corrección de error** cuando Kiro te pregunte cuál es tu intención.
4. Siga el flujo de trabajo a través del análisis, diseño e implementación.

---

### Más información

- [Mejores prácticas para especificaciones de corrección de errores →](https://kiro.dev/docs/specs/best-practices/#bugfix-specs)
- [Corrección con pruebas basadas en propiedades →](https://kiro.dev/docs/specs/correctness/)

---

*📂 Capítulo: **Specs > Correctness***

## Corrección con pruebas basadas en propiedades

> **Fuente:** [kiro.dev/docs/specs/correctness/](https://kiro.dev/docs/specs/correctness/)

---

Kiro utiliza pruebas basadas en propiedades (PBT) para validar que su implementación realmente coincida con lo que definió en sus especificaciones. Este enfoque genera cientos o miles de casos de prueba automáticamente, detectando casos extremos que nunca escribiría manualmente.

---

### Conceptos

#### ¿Qué es una propiedad?

Una propiedad es una **declaración universal** sobre cómo debe comportarse su sistema. Las propiedades expresan las invariantes y contratos que siempre deben ser verdaderos en su sistema, independientemente de los datos específicos involucrados.

> *"Para cualquier usuario autenticado y cualquier listado activo, el usuario puede ver ese listado."*

Esto captura una regla general sobre el comportamiento del sistema que debe cumplirse en todos los escenarios válidos. En el mundo de las especificaciones de Kiro, esto se corresponde directamente con los requisitos de EARS.

#### Cómo funcionan las pruebas basadas en propiedades

**Prueba tradicional:**
- El usuario agrega el Auto #5 a favoritos → El Auto #5 aparece en su lista

**Prueba basada en propiedades:**
- CUANDO cualquier usuario agregue un automóvil a favoritos, EL Sistema LO mostrará en su lista

PBT prueba esto automáticamente con:
- Usuario A agregando el Auto #1
- Usuario B añadiendo el coche n.º 500
- Usuarios con caracteres especiales en los nombres.
- Coches con varios estados.
- Cientos de combinaciones más

Esto detecta casos extremos y verifica que la implementación coincida con la intención.

A lo largo de este proceso, PBT busca contraejemplos mediante la **"reducción"**, casi como un equipo rojo que intenta descifrar su código. Cuando encuentra infracciones, Kiro puede actualizar automáticamente su implementación o las opciones de superficie para corregir la especificación, la implementación o la prueba.

---

### Pruebas basadas en propiedades con especificaciones

#### Flujo de trabajo

Kiro extrae propiedades de sus requisitos formateados en EARS:

1. Identifica requisitos como *"EL Sistema DEBE permitir a los usuarios autenticados ver listados de automóviles activos"*
2. Determina qué propiedades se pueden probar lógicamente.
3. Genera cientos o miles de casos de prueba aleatorios cuando elige ejecutarlos.

#### Fase de diseño

En la fase de diseño, Kiro:
- Extrae propiedades de sus requisitos.
- Genera casos de prueba.
- Al pasar el cursor sobre una propiedad se revela su conexión con el requisito original y la tarea vinculada.

#### Ejecutando tareas

En la fase de ejecución, Kiro ejecuta los casos PBT generados en su implementación.

> **Nota:** Los PBT son **opcionales de forma predeterminada** para que pueda concentrarse primero en su implementación principal. Una vez que se ejecuta una prueba de propiedad, puede ver la referencia al código generado.

Cuando falla una prueba de propiedad, Kiro:
1. Identifica el escenario de falla específico y lo presenta para su revisión.
2. Te permite chatear con Kiro para entender el fallo.
3. Le permite determinar la solución adecuada, ya sea actualizando la implementación, ajustando la prueba o refinando el requisito en sí.

---

*📂 Capítulo: **Specs > Best practices***

## Mejores prácticas: especificaciones

> **Fuente:** [kiro.dev/docs/specs/best-practices/](https://kiro.dev/docs/specs/best-practices/)

---

### Especificaciones de funciones

#### ¿Qué flujo de trabajo debo elegir?

Las especificaciones de funciones admiten dos flujos de trabajo: **Requisitos primero** y **Diseño primero**.

| Elija Requisitos: primero cuando... | Elija Diseño primero cuando... |
|---|---|
| Conoces el comportamiento del sistema que quieres construir | Tiene un diseño técnico o arquitectura existente |
| La arquitectura es flexible y puede diseñarse para satisfacer las necesidades | El sistema debe cumplir estrictos requisitos no funcionales |
| Creación de características de productos impulsadas por los comentarios de los clientes | Creación de prototipos con una pila tecnológica específica |
| Empezar sin limitaciones técnicas | Explorando la viabilidad técnica antes de comprometerse con el alcance |

#### ¿Puedo cambiar los flujos de trabajo después de iniciar una especificación?

No, debes elegir un flujo de trabajo al crear la especificación. Si necesita cambiar los enfoques, cree una nueva especificación de función con el flujo de trabajo deseado. Puede copiar contenido relevante de la especificación anterior si es necesario.

#### ¿Puedo utilizar ambos flujos de trabajo para el mismo proyecto?

¡Sí! Puede crear varias especificaciones. Por ejemplo:
1. Utilice Design-First para validar la viabilidad técnica
2. Cree una especificación de requisitos primero para el desarrollo completo de funciones.

#### ¿Cómo importo diseños o arquitectura existentes?

- **Usando el flujo de trabajo Diseño-Primero:** Cree una nueva especificación de característica y seleccione Diseño-Primero, cargue diagramas de arquitectura (PNG, JPG) o pegue el contenido del diseño, Kiro formalizará el diseño en `design.md`.
- **Usar imágenes:** Exporte diagramas desde herramientas como draw.io, Lucidchart o tome fotografías de bocetos de pizarra e inclúyalas en su mensaje inicial.
- **Usando la integración MCP:** Si su herramienta de diseño tiene un [servidor MCP](https://kiro.dev/docs/mcp), puede conectarse directamente para importar diseños.

#### ¿Cómo importo los requisitos existentes?

- **Usando la integración MCP:** Si su herramienta de requisitos tiene un servidor MCP (JIRA, Confluence, etc.), conéctese directamente para importar requisitos en su sesión de especificaciones.
- **Importación manual:** Copie sus requisitos existentes en un nuevo archivo en su repositorio y abra una sesión de chat de especificaciones:
  ```
  #foo-prfaq.md Genera una especificación a partir de él
  ```

#### ¿Cómo repito mis especificaciones de funciones?

Continúe la sesión de chat de especificaciones para perfeccionar los requisitos, actualizar el diseño o ajustar las tareas. Kiro mantiene el contexto de su especificación durante toda la conversación.

---

### Especificaciones de corrección de errores

#### ¿Cómo escribo una buena descripción de error?

Una descripción clara del error ayuda a Kiro a realizar un análisis preciso de la causa raíz. Incluir:

1. **Pasos de reproducción**: describe las condiciones exactas que desencadenan el error.
2. **Comportamiento actual**: lo que hace el sistema ahora (el defecto)
3. **Comportamiento esperado**: qué debería hacer el sistema en su lugar
4. **Restricciones**: cualquier código o comportamiento que no debe cambiar

**Ejemplo de mensaje:**
```
Cuando un usuario envía un formulario con caracteres especiales en el campo de nombre (por ejemplo, O'Brien),
la API devuelve un error 500. Debería aceptar la entrada y guardarla correctamente.
La lógica de validación de los campos de correo electrónico y contraseña no debería verse afectada.
```

#### ¿Cómo evito regresiones con Bugfix Specs?

Las especificaciones de corrección de errores capturan explícitamente el "comportamiento sin cambios" junto con la corrección. Durante la fase de análisis documentar lo que se debe seguir trabajando:

```
- WHEN [condition] THEN the system SHALL CONTINUE TO [existing behavior]
```

Kiro genera pruebas basadas en propiedades que validan tanto la corrección como la preservación del comportamiento existente.

#### ¿Cuándo debo utilizar una especificación de corrección de errores frente a una solución rápida?

**Utilice una especificación de corrección de errores cuando:**
- El error está en una ruta de código crítica.
- Los intentos de reparación anteriores provocaron regresiones.
- La causa raíz no es inmediatamente obvia.
- Necesita documentación para el cumplimiento o conocimiento del equipo.

**Una solución rápida en el chat está bien para:** errores tipográficos, errores lógicos simples o cambios de una línea bien entendidos.

#### ¿Puedo convertir una especificación de corrección de errores en una especificación de función?

No directamente. Si el análisis de la causa raíz revela que la solución requiere una nueva funcionalidad significativa, cree una especificación de característica separada y mantenga la especificación de corrección de errores centrada en el defecto original.

---

### General

#### ¿Cómo comparto especificaciones con mi equipo?

Las especificaciones están diseñadas para ser controladas por versiones. Almacene las especificaciones directamente en el repositorio de su proyecto junto con el código que describen. Esto mantiene todos los artefactos del proyecto juntos y mantiene la conexión entre los requisitos y la implementación.

#### ¿Puedo compartir especificaciones entre varios equipos?

Sí, aprovechando los submódulos de Git o las referencias de paquetes:
1. Cree un repositorio central de especificaciones
2. Utilice submódulos de Git o referencias de paquetes para vincular especificaciones a proyectos individuales.
3. Implementar flujos de trabajo entre repositorios para proponer, revisar y actualizar especificaciones compartidas.

#### ¿Puedo iniciar una sesión de especificaciones desde una sesión de vibración?

Sí. En una conversación de ambiente, diga "Generar especificaciones". Kiro te preguntará si deseas iniciar una sesión de especificaciones y generará requisitos basados ​​en el contexto de tu sesión de vibración.

#### ¿Puedo ejecutar todas las tareas de mi especificación de una sola vez?

Sí. Haga clic en el botón **"Ejecutar todas las tareas"** en su archivo `tasks.md`. Nota: esto solo ejecutará tareas incompletas que estén marcadas como requeridas.

#### ¿Qué pasa si algunas tareas ya están implementadas?

**Opción 1:** Haga clic en **"Actualizar tareas"** en su archivo `tasks.md`; Kiro marcará automáticamente las tareas completadas.

**Opción 2:** En una sesión de especificaciones, pregúntele a Kiro: *"Compruebe qué tareas ya están completas"*: Kiro analizará su código base y marcará las tareas completadas.

#### ¿Cómo hago referencia a una especificación en el chat?

Utilice el proveedor de contexto `#spec`. Escriba `#spec` y presione Entrar para ver una lista de especificaciones disponibles, luego seleccione la que desea incluir. Kiro incluye automáticamente todos los archivos de especificaciones (`requirements.md`, `design.md` y `tasks.md`) en el contexto de la conversación.

#### ¿Cuántas especificaciones puedo tener en un solo repositorio?

No hay un límite estricto. Organice las especificaciones de forma lógica dentro de `.kiro/specs/` usando nombres descriptivos para cada característica o corrección de errores.

---

*📂 Capítulo: **Chat > Autopilot***

## Charlar

> **Fuente:** [kiro.dev/docs/chat/](https://kiro.dev/docs/chat/)

---

La interfaz de chat de Kiro es la forma principal de interactuar con el agente de IA para conversaciones contextuales, asistencia para el desarrollo y generación de código.

---

### Empezando

#### Accediendo al chat

| Método | Atajo |
|---|---|
| Atajo de teclado | `Cmd+L` (Mac) / `Ctrl+L` (Windows/Linux) |
| Paleta de comandos | `Cmd+Shift+P` → buscar "Kiro: Abrir Chat" |
| Barra lateral secundaria | `Cmd+Opción+B` (Mac) / `Ctrl+Alt+B` (Windows/Linux) |

#### Soporte multilingüe

Kiro chat admite múltiples idiomas naturales, incluidos: mandarín, francés, alemán, italiano, japonés, español, coreano, hindi, portugués y más. Kiro detecta automáticamente tu idioma y responde en el mismo idioma.

#### Tu primera conversación

1. Escriba su pregunta o solicitud en lenguaje natural en la entrada del chat.
2. Presione **Entrar** para enviar
3. Kiro analizará tu solicitud y responderá adecuadamente

**Solicitudes de ejemplo:**
```
"Explica cómo funciona la autenticación en este proyecto"
"Crear un componente React para una página de perfil de usuario"
"Ayúdame a corregir el error en esta función"
```

#### Exportar una conversación

Haga clic derecho en la pestaña de la conversación → **Exportar conversación** → guarda como formato `.md`.

#### Detección inteligente de intenciones

Kiro detecta inteligentemente tu intención:
- **Solicitudes de información** ("¿Cómo funciona esto?", "¿Cuál es el propósito de este código?") → Responde con explicaciones sin modificar el código.
- **Solicitudes de acción** ("Crear un componente", "Corregir este error") → Propone o implementa cambios de código

---

### Gestión del contexto

#### Proveedores de contexto

Utilice el símbolo `#` en la entrada del chat para acceder a los proveedores de contexto:

| Proveedor | Uso de ejemplo |
|---|---|
| `#base de código` | `#codebase explica el flujo de autenticación` |
| `#archivo` | `#auth.ts explica esta implementación` |
| `#carpeta` | `#componentes/ ¿qué componentes tenemos?` |
| `#git diff` | `#git diff explica qué cambió en este PR` |
| `#terminal` | `#terminal ayúdame a corregir este error de compilación` |
| `#problemas` | `#problemas me ayudan a resolver estos problemas` |
| `#url` | `#url:https://docs.example.com/api explica esta API` |
| `#código` | `#código: suma constante = (a, b) => a + b; explica esta función` |
| `#repositorio` | `#repositorio ¿cómo está organizado este proyecto?` |
| `#actual` | `#actual explica este componente` |
| `#dirección` | `#steering:coding-standards.md revisa mi código` |
| `#docs` | `#docs:api-reference.md explica este punto final de API` |
| `#especificación` | `#spec: la autenticación de usuario actualiza el archivo de diseño` |
| `#mcp` | `#mcp:aws-docs ¿Cómo configuro los depósitos S3?` |

Combine múltiples proveedores de contexto:
```
##codebase #auth.ts explica cómo funciona la autenticación con nuestra base de datos
```

El proveedor de contexto `#terminal` es particularmente poderoso para la depuración:
```
##terminal Mi compilación está fallando, ¿cuál es el problema?
##terminal Estas pruebas no pasan, ayúdame a entender por qué
##terminal npm install arroja errores
```

---

### Sesiones e Historia

#### Gestión de sesiones

- **Nueva sesión:** Haga clic en el ícono **+** en el panel de chat.
- **Cambiar de sesión:** Navega usando el selector de pestañas
- **Ver historial:** Haga clic en el botón **Historial**
- **Seguimiento de tareas:** Supervise el progreso mediante el botón **Lista de tareas**

#### Historial de ejecución

Kiro mantiene un historial detallado de las sesiones que incluye: cambios de código, comandos ejecutados, resultados de búsqueda y operaciones de archivos. Puede **buscar**, **restaurar** o **eliminar** sesiones específicas.

---

*📂 Capítulo: **Chat > Autopilot***

## piloto automático

> **Fuente:** [kiro.dev/docs/chat/autopilot/](https://kiro.dev/docs/chat/autopilot/)

---

El modo de piloto automático es el modo de ejecución autónoma de Kiro que permite al agente realizar cambios de código en su base de código y completar tareas complejas con una intervención mínima.

---

### ¿Qué es el modo de piloto automático?

El modo de piloto automático permite a Kiro trabajar de forma más independiente en su nombre: creando archivos, modificando código en múltiples ubicaciones, ejecutando comandos y tomando decisiones arquitectónicas sin pedir aprobación en cada paso.

---

### Cómo funciona

#### Modo piloto automático *(predeterminado)*

Kiro trabaja **de forma autónoma** para completar las tareas de un extremo a otro:
- Puede crear archivos, modificar código en múltiples ubicaciones y ejecutar comandos
- Toma decisiones arquitectónicas sin pedir aprobación en cada paso.
- Mantienes el control mediante la capacidad de ver todos los cambios, revertir todo o interrumpir en cualquier momento.

#### Modo supervisado

Kiro trabaja **paso a paso** con tu aprobación:
- Rinde para su aprobación después de cada turno que contiene ediciones de archivos
- Los cambios se presentan como **fragmentos individuales** (grupos lógicos de líneas relacionadas)
- Cada trozo puede ser aceptado, rechazado o discutido de forma independiente con el chat en línea
- Puede aceptar cambios a nivel de archivo o aceptar todos los cambios a la vez
- Visibilidad total de cada cambio; control detallado sobre el proceso de desarrollo

---

### Cambiar entre modos

Puede **alternar entre modos en cualquier momento** en la interfaz de chat según sus necesidades actuales y su nivel de comodidad con la tarea en cuestión.

---

### Cuándo usar cada modo

| Modo | Mejor para |
|---|---|
| **Piloto automático** | Usuarios experimentados familiarizados con Kiro, tareas repetitivas o bien definidas, proyectos en los que desea avanzar rápidamente, tareas que abarcan varios archivos o requieren varios pasos |
| **Supervisado** | Nuevos usuarios que se familiarizan con Kiro, bases de código críticas o sensibles, aprenden cómo Kiro aborda los problemas, cuándo desean revisar cuidadosamente cada cambio, trabajan con sistemas complejos o desconocidos |

---

### Funciones de gestión de cambios

#### En modo piloto automático

Mantienes el control a través de varias características clave:

| Característica | Descripción |
|---|---|
| **Ver todos los cambios** | Seleccione "Ver todos los cambios" en el módulo de Chat para ver una diferencia completa de todas las modificaciones |
| **Revertir todos los cambios** | Seleccione "Revertir" para restaurar todos los archivos a su estado anterior localmente (esencialmente para deshacer todas las modificaciones de Kiro) |
| **Revertir punto de control** | Revertir a un [punto de control](https://kiro.dev/docs/chat/checkpoints): revierte tanto los cambios de archivos como las adiciones de contexto |
| **Interrumpir ejecución** | Detenga a Kiro en mitad de la ejecución en cualquier momento para recuperar el control manual |

#### En modo supervisado

| Característica | Descripción |
|---|---|
| **Revisar cambios** | Kiro muestra exactamente lo que se modificó, con indicadores de cambio de línea (líneas +x -y) visibles en el chat |
| **Revisión por archivo** | Cuando se editan varios archivos, revise y acepte/rechace los cambios por archivo |
| **Revisión basada en trozos** ​​| Para modificaciones de archivos, Kiro presenta los cambios como partes individuales que pueden aceptarse, rechazarse o discutirse de forma independiente.
| **Acciones por trozo** | Aceptar, rechazar o chatear en línea sobre cualquier trozo específico |
| **Aprobación selectiva** | Aceptar algunos trozos y rechazar otros dentro del mismo archivo |
| **Aceptar todo/Rechazar todo** | Aceptar todo aplica todos los cambios pendientes y continúa; Rechazar todo revierte todo |

---

*📂 Capítulo: **Chat > Vibe vs. Spec***

## Sesiones de vibración frente a especificaciones

> **Fuente:** [kiro.dev/docs/chat/vibe/](https://kiro.dev/docs/chat/vibe/)

---

Kiro ofrece dos modos de sesión en el chat: **Vibe** (conversacional) y **Spec** (estructurado). Cada uno está diseñado para diferentes tipos de tareas.

---

### Sesión de vibración

Las sesiones Vibe son sesiones interactivas enfocadas en Q&A, diseñadas para preguntas rápidas, explicaciones y construcción de proyectos a través de un enfoque más conversacional.

#### Cómo acceder

- Abre el chat de Kiro (`Cmd+L` / `Ctrl+L`)
- El modo por defecto es **Vibe**
- Escribe tu pregunta o solicitud en lenguaje natural.

#### Cuándo vibrar

- Preguntas rápidas sobre el código
- Explicaciones y documentación.
- Refactorizaciones simples
- Explorar opciones o alternativas
- Depuración conversacional
- Cualquier tarea donde el proceso no necesite ser estructurado

---

### Sesión de especificaciones

Una sesión Spec guía a través de un enfoque estructurado para tareas de desarrollo complejos. Formaliza el proceso de desarrollo de software, transformando ideas de alto nivel en planos de implementación detallados con ejecución sistemática y seguimiento claro.

#### Cómo acceder

- En el chat, cambia al modo **Spec** usando el selector de modo
- O usa la paleta de comandos: `Cmd+Shift+P` → `Kiro: Open Spec`

#### Cuándo especificar

- Nuevas funcionalidades complejas
- Cambios arquitectónicos
- Tareas que requieren múltiples fases: requisitos → diseño → tareas
- Cuando necesitas trazabilidad y seguimiento del progreso
- Proyectos en equipo donde la documentación del proceso importa

---

### Comparación rápida

| | Ambiente | Especificaciones |
|---|---|---|
| **Estilo** | Conversacional | Estructurado |
| **Ideal para** | Preguntas, ajustes, exploración | Funcionalidades complejas, arquitectura |
| **Salida** | Respuesta directa + código | Documento de requisitos → Documento de diseño → Lista de tareas |
| **Controlar** | Libre | Paso a paso con aprobaciones |
| **Seguimiento** | Ninguno | Seguimiento de finalización de tareas |

---

*📂 Capítulo: **Chat > Slash commands***

## Comandos de barra diagonal

> **Fuente:** [kiro.dev/docs/chat/slash-commands/](https://kiro.dev/docs/chat/slash-commands/)

---

Los comandos de barra diagonal permiten acceder rápidamente a hooks y archivos de Steering directamente desde la entrada del chat escribiendo `/`.

---

### Cómo funciona

1. Escribí `/` en el campo de entrada del chat
2. Navegá o buscá los comandos disponibles
3. Seleccione un comando y presione **Entrar**

---

### Tipos de comandos

#### Hooks

Los [Hooks](../07_Hooks/01_Hook triggers.md) con disparador de tipo **Manual** aparecen en el menú de comandos de barra diagonal. Al seleccionar uno, Kiro lo ejecuta inmediatamente en la sesión actual.

**Ejemplos:**
```
/sincronizar-fuente-con-docs
/ejecutar-pruebas
/generar-registro de cambios
```

➡️ Para agregar un comando de gancho como barra diagonal: configure su tipo de disparador en **Manual**. Ver [Disparadores de gancho →](../07_Hooks/01_Hook%20triggers.md)

---

#### Archivos de Steering

Los [archivos de Steering](../08_Steering.md) configurados con `inclusion: manual` en el frontmatter aparecen como comandos de barra diagonal. A diferencia del volante siempre activo (que se incluye automáticamente en toda conversación), el volante manual te permite incorporar guías específicas **solo cuando las necesidades**.

Al seleccionar uno, el contenido del archivo se agrega al contexto de tu conversación actual.

**Ejemplos:**
```
/accesibilidad
/revisión-de-código
/rendimiento
/refactorizar
/pruebas
```

➡️ Para agregar un archivo de Steering como comando de barra diagonal, configurará en el frontmatter:

```markdown
---
inclusion: manual
---
```

Ver [Dirección →](../08_Steering.md)

---

### Mejores prácticas

- **Nombres descriptivos** — Nombres claros como `/run-e2e-tests` o `/accessibility` hacen que los comandos sean fáciles de encontrar
- **Cambio de contexto** — Creará archivos de Steering para diferentes flujos de trabajo (frontend, backend, pruebas) y cambiará entre ellos según sea necesario
- **Combiná con `#` proveedores** — Los comandos de barra diagonal funcionan junto a los [context Providers](./01_Autopilot.md) (`#file`, `#codebase`, etc.) para máximo control

---

### Relacionado

- [Hooks →](../07_Hooks/01_Hook%20triggers.md)
- [Dirección →](../08_Steering.md)
- [Terminal →](./04_Terminal.md)

---

*📂 Capítulo: **Chat > Terminal***

## Integración de terminales

> **Fuente:** [kiro.dev/docs/chat/terminal/](https://kiro.dev/docs/chat/terminal/)

---

En lugar de memorizar sintaxis de comandos o cambiar entre ventanas, describe lo que quieres hacer y Kiro traduce tus solicitudes en comandos ejecutables, mantiene el contexto entre operaciones y proporciona un sistema de aprobación seguro.

---

### Empezando

Simplemente describí lo que querés hacer en lenguaje natural:

- "Instalar las dependencias del proyecto"
- "Verificar el estado de git"
- "Buscar todos los archivos TypeScript en la carpeta src"
- "Ejecutar el servidor de desarrollo"

Kiro traduce tu solicitud al comando apropiado y pide aprobación antes de ejecutar.

---

### Cómo funciona

Cuando Kiro sugiere un comando, tenés cuatro opciones:

| Opción | Acción |
|---|---|
| **Modificar** | Editar el comando antes de ejecutar |
| **Rechazar** | Cancelar la ejecución |
| **Ejecutar** | Ejecutar una vez |
| **Corre y confía** | Ejecutar y confiar en comandos similares en el futuro |

Los comandos de larga ejecución (como servidores de desarrollo) son gestionados automáticamente por Kiro en terminales dedicadas sin bloquear tu flujo de trabajo.

---

### Aprobación y seguridad de comandos

#### Comandos de confianza

Configurará qué confiar comandos automáticamente en:
**Configuración → Kiro Agent: Comandos confiables**

Disponible a nivel usuario (global) y a nivel espacio de trabajo.

##### Coincidencia exacta
```json
["instalación npm", "estado de git"]
```
- ✅ `npm install` → aprobado automáticamente
- ✅ `git status` → aprobado automáticamente
- ❌ `npm install --save` → requiere aprobación (solo coincidencia exacta)

##### Coincidencia parcial de comodines
```json
["instalación npm *"]
```
- ✅ `npm install` → aprobado
- ✅ `npm install --save` → aprobado
- ✅ `npm install express` → aprobado
- ❌ `npm run build` → requiere aprobación

##### Coincidencia completa de comodines
```json
["npm *", "git *"]
```
- ✅ Todos los comandos `npm` y `git` → auto-aprobado
- ❌ `docker build.` → requiere aprobación

##### Confianza universal
```json
["*"]
```
> ⚠️ **Extremadamente peligroso.** Solo usá esto si controlás completamente el ambiente.

#### Lista de denegaciones de comandos

La lista de denegación impide la aprobación automática de comandos con patrones específicos, independientemente de los ajustes de confianza. Estados Unidos **coincidencia de subcadenas**.

**Configuración → Agente Kiro: Lista de comandos rechazados**

```json
{
  "kiroAgent.commandDenylist": [
    "rm -rf",
    "sudo",
    "chmod 777",
    "eval",
    "curl | sh",
    "wget | sh",
    "> /dev/",
    "mkfs",
    "dd if="
  ]
}
```

> La lista de denegados **se revisa antes** que los ajustes de confianza. Incluso con `["*"]` entrust, los comandos denegados requieren aprobación manual.

---

### Usando el contexto del terminal

Referencia la salida reciente de tu terminal con `#terminal`:

```
##terminal analyze the error from the last npm run build
```

> ⚠️ `#terminal` siempre hace referencia a la terminal activa/visible. Si tiene múltiples terminales abiertos, asegúrese de que la correcta esté activada antes de usar `#terminal`.

**Capacidad:**
- Análisis de errores — Entender por qué fallaron los comandos
- Interpretación de salida — Explicar resultados complejos y logs
- Acciones de seguimiento — Sugerir próximos pasos basados en resultados reales
- Reconocimiento de patrones — Identificar problemas recurrentes
- Depuración del entorno — Resolver conflictos de sistema y dependencias

---

*📂 Capítulo: **Chat > Dev servers***

## Servidores de desarrollo

> **Fuente:** [kiro.dev/docs/chat/dev-servers/](https://kiro.dev/docs/chat/dev-servers/)

---

El soporte del servidor de desarrollo permite al agente Kiro ejecutar procesos en segundo plano para acceder a comandos de larga ejecución sin bloquear tu flujo de trabajo. En lugar de manejar múltiples ventanas de terminal, podés pedirle a Kiro que lo maneje todo.

---

### Cómo funciona

![Iniciar proceso](https://kiro.dev/videos/start-process.mp4)

Cuando pides a Kiro ejecutar un comando de larga ejecución, automáticamente:

1. Crea una terminal dedicada con un nombre descriptivo (ej. `"Kiro: npm run dev"`)
2. Inicia el proceso en segundo plano
3. Retorna el control inmediatamente para que puedas seguir trabajando
4. Rastrea el proceso para que puedas consultar su estado o salida en cualquier momento

Los procesos en segundo plano:
- Son visibles en tu lista de terminales
- Muestran el comando que están ejecutando
- Persistir hasta que los detengas o cierres Kiro

---

### Iniciar un servidor de desarrollo

Pedíselo en lenguaje natural:

- "Iniciar el servidor de desarrollo"
- "Ejecutar npm ejecutar reloj"
- "Iniciar el observador de compilación del paquete web"

#### Reutilización de procesos

Kiro detecta cuando un proceso similar ya está corriendo y puede reutilizarlo en lugar de crear uno nuevo, evitando conflictos de puerto.

---

### Salida del proceso de monitoreo

Consultará el estado de tus procesos en cualquier momento:

- "Verificar la salida del servidor de desarrollo"
- "¿Qué muestra el proceso de vigilancia de ejecución de npm?"
- "¿Hay algún error en el observador de compilación?"

Kiro puede:
- Identificar errores de compilación y sugerir correcciones
- Confirmar que los servidores se iniciaron correctamente
- Depurar problemas analizando mensajes de error
- Monitorear el progreso de tareas largas

---

### Gestión de procesos

| Acción | Ejemplo |
|---|---|
| **Listar procesos activos** | "¿Qué procesos se están ejecutando?" |
| **Detener un proceso** | "Detener el servidor de desarrollo" |
| **Terminar todos** | "Eliminar todos los procesos en segundo plano" |

---

### Automatización con dirección

Podés configurar Kiro para verificar procesos automáticamente con reglas de dirección:

```markdown
## Development Workflow
After making code changes:
1. Always check the output of the `npm run dev` process
2. Look for compilation errors or warnings
3. If errors exist, suggest fixes before proceeding
```

---

### Combinación con diagnóstico de código

Los procesos en segundo plano funcionan junto con la herramienta de diagnósticos de Kiro:

- **Dev server / Build watcher** → captura de errores de compilación en tiempo de ejecución
- **Herramienta de diagnóstico** → detecta errores de tipo, advertencias de pelusa y problemas de análisis estático

Pedilos juntos: *"Verifique el resultado del observador de compilación y muéstreme cualquier error de TypeScript"*

---

### Casos de uso comunes

| Caso | Ejemplo |
|---|---|
| **Servidores de desarrollo** | Next.js, React, Vite dev server mientras codificas |
| **Construir observadores** | paquete web, TypeScript, esbuild en modo reloj |
| **Corredores de prueba** | Vitest, Jest en modo watch para feedback continuo |

---

*📂 Capítulo: **Chat > Diagnostics tool***

## Herramienta de diagnóstico

> **Fuente:** [kiro.dev/docs/chat/diagnostics/](https://kiro.dev/docs/chat/diagnostics/)

---

La herramienta de diagnóstico de Kiro ayuda al agente a entender y trabajar con tu código integrándose con las extensiones del IDE. Proporciona detección de errores en tiempo real, validación de sintaxis y análisis de código que mejora la calidad de la asistencia AI.

---

### Descripción general

La integración con extensiones del IDE proporciona:

- **Detección de errores en tiempo real** — Errores de sintaxis, discrepancias de tipos y problemas de compilación
- **Información específica del idioma** — Semántica del lenguaje, importaciones y dependencias
- **Análisis de calidad de código** — Reglas de linting, violaciones de estilo y mejores prácticas
- **Conciencia contextual** — Estructura del proyecto, APIs disponibles y definiciones de tipos

---

### Cómo funciona

La herramienta de diagnóstico se integra con las extensiones de lenguaje instaladas. Cuando tenga extensiones de lenguaje instaladas, Kiro accede a la información diagnóstica del servidor de lenguaje para entender mejor su código.

La herramienta funciona **automáticamente durante la ejecución del agente** — sin configuración adicional necesaria.

---

### Empezando

1. **Instalar extensiones de lenguaje** para tus lenguajes de programación:
   - [Guía de Python →](https://kiro.dev/docs/guides/languages-and-frameworks/python-guide/#extensions)
   - [Guía de TypeScript/JavaScript →](https://kiro.dev/docs/guides/languages-and-frameworks/typescript-javascript-guide/#suggested-extensions)
   - [Guía de Java →](https://kiro.dev/docs/guides/languages-and-frameworks/java-guide/#suggested-extensions)

2. **Abrir un archivo** en tu lenguaje objetivo para activar el servidor de idiomas

La herramienta funciona automáticamente a partir de ese punto.

---

### Solución de problemas

Si el agente no detecta problemas de código:

| Problema | Solución |
|---|---|
| Extensión no detectada | Verificar que la extensión está habilitada en el panel de Extensiones |
| Servidor de idiomas inactivo | Panel de salida → buscar mensajes de error de servidores de idiomas |
| Servidor no iniciado | Paleta de comandos → "Recargar ventana" |
| Capacidades desactualizadas | Mantener extensiones actualizadas |

---

### Próximos pasos

- [Guías de idiomas →](https://kiro.dev/docs/guides/languages-and-frameworks) para configuración por idioma
- [Combinación de diagnósticos con servidores de desarrollo →](https://kiro.dev/docs/chat/dev-servers/#combining-with-code-diagnostics) para un flujo de trabajo completo

---

*📂 Capítulo: **Chat > Agent notifications***

## Notificaciones de agentes

> **Fuente:** [kiro.dev/docs/chat/notifications/](https://kiro.dev/docs/chat/notifications/)

---

Las notificaciones del agente se mantienen informadas sobre el progreso y las del agente Kiro, especialmente cuando trabaja en segundo plano o en tareas de larga duración.

---

### Descripción general

Cuando Kiro trabaja en modo Autopilot ejecutando tareas complejas, las notificaciones te permiten:

- Saber cuándo completó una tarea o fase
- Ser alertado si el agente encuentra un problema y necesita su información
- Monitorear el progreso sin necesidad de mantener el chat en foco

---

### Tipos de notificación

| Tipo | Cuándo ocurre |
|---|---|
| **Tarea completa** | El agente terminó un turno o tarea |
| **Se requiere aprobación** | El agente necesita tu aprobación para continuar |
| **Error** | El agente encontró un error que no puede resolver solo |
| **Proceso en segundo plano** | Un servidor de desarrollo o proceso en segundo plano reporta estado |

---

### Relacionado

- [Autopilot →](./02_Autopilot.md) — Modo autónomo donde las notificaciones son más relevantes
- [Dev Servers →](./05_Dev servers.md) — Procesos en segundo plano que generan notificaciones
- [Checkpoints →](./08_Checkpoints.md) — Puntos de control para revertir cambios

---

*📂 Capítulo: **Chat > Checkpoints***

## puntos de control

![Puntos de control](https://kiro.dev/videos/checkpoints.mp4)

> **Fuente:** [kiro.dev/docs/chat/checkpoints/](https://kiro.dev/docs/chat/checkpoints/)

---

Los puntos de control permiten realizar cambios realizados por Kiro a través de múltiples turnos, incluyendo tanto cambios en archivos como adiciones de contexto.

---

### Descripción general

Cada vez que el agente Kiro modifica uno o más archivos y completa su turno, aparece inmediatamente arriba del cuadro de entrada del chat la opción de **Revertir** los cambios realizados.

---

### Reversiones frente a puntos de control

| | Revertir | Punto de control |
|---|---|---|
| **Alcance temporal** | Solo el último turno del agente | Múltiples turnos |
| **Qué deshace** | Solo cambios en archivos | Cambios en archivos **y** adiciones de contexto |
| **Cómo acceder** | Botón "Revertir" sobre la entrada | Selector de punto de control en el historial |

---

### Cómo utilizar los puntos de control

1. Kiro crea un checkpoint automáticamente antes de cada turno que modifica archivos
2. Para revertir a un checkpoint anterior, busque el icono de checkpoint en el historial del chat
3. Selecciona el checkpoint al que quieres volver
4. Kiro deshará todos los cambios en archivos y eliminará las adiciones de contexto realizadas desde ese punto

---

### Mejores prácticas

- Usá **Revert** para deshacer solo el último paso
- Usá **Checkpoints** cuando querés volver a un estado anterior luego de Múltiples pasos del agente
- Los puntos de control son especialmente útiles en el flujo de trabajo de Autopilot donde el agente ejecuta muchos cambios seguidos

---

### Relacionado

- [Autopilot →](./02_Autopilot.md) — donde los puntos de control son más útiles
- [Resumen →](./09_Summarization.md) — gestión del contexto de conversación

---

*📂 Capítulo: **Chat > Summarization***

## Resumen

> **Fuente:** [kiro.dev/docs/chat/summarization/](https://kiro.dev/docs/chat/summarization/)

---

### Descripción general

Todos los modelos de lenguaje tienen una "ventana de contexto" — la cantidad máxima de texto que el modelo puede manejar al mismo tiempo. El tamaño varía según el modelo.

Cuando tengas una conversación con Kiro, recuerda y envía todos los mensajes anteriores como contexto al modelo. A medida que la conversación se alarga, eventualmente se acerca al límite de la ventana de contexto.

---

### Resumen automático

Cuando el uso del contexto alcanza el **80% del límite del modelo**, Kiro **automáticamente resumirá** todos los mensajes de la conversación para que la longitud del contexto vuelva a estar por debajo del límite.

Podés monitorear el uso actual del contexto con el **medidor de uso de contexto** en el panel del chat.

---

### Medidor de uso de contexto

El medidor en el panel del chat muestra en tiempo real qué porcentaje de la ventana de contexto del modelo está siendo utilizado. Usalo para anticiparte a la resumen automática antes de que ocurra.

---

### Relacionado

- [Checkpoints →](./08_Checkpoints.md) — Los checkpoints pueden verse afectados por la resumen
- [Autopilot →](./02_Autopilot.md) — En Autopilot, la resumen ocurre más frecuentemente en tareas largas

---

*📂 Capítulo: **Chat > Subagents***

## Subagentes

![Subagentes](https://kiro.dev/videos/subagents.mp4)

> **Fuente:** [kiro.dev/docs/chat/subagents/](https://kiro.dev/docs/chat/subagents/)

---

Los subagentes permiten a Kiro ejecutar tareas en paralelo y delegar trabajo especializado a agentes apropiados.

---

### Descripción general

Kiro puede crear subagentes para manejar tareas complejas de forma independiente. Cada subagente opera con su propio contexto y conjunto de herramientas, reportando resultados al agente principal.

---

### Subagentes personalizados

Podés definir tu propio agente personalizado creando un archivo Markdown (`.md`) en:

- `~/.kiro/agents/` — alcance global (disponible en todos los espacios de trabajo)
- `<workspace>/.kiro/agents/` — alcance del espacio de trabajo (solo en ese proyecto)

El aviso del agente va en el cuerpo del archivo. Los atributos adicionales se definen como materia frontal de YAML.

#### Ejemplo: Agente revisor de código

Crear `~/.kiro/agents/code-reviewer.md`:

```markdown
---
nombre: revisor de código
Descripción: Asistente experto en revisión de código.
herramientas: ["leer", "@ contexto7"]
modelo: claude-soneto-4
---

Eres un revisor de código senior.

### Tus responsabilidades
- Revisar el código para comprobar su corrección, rendimiento y seguridad.
- Sugerir mejoras con ejemplos.
- Verificar antipatrones comunes
```

#### Invocación

Kiro invoca automáticamente el subagente cuando detecta que la tarea encaja con su descripción, o podés invocarlo explícitamente:

```
> Use the code-reviewer agent to review this PR
```

#### Atributos (antecedentes de YAML)

| Campo | Descripción |
|---|---|
| `nombre` | Nombre único del agente |
| `descripción` | Descripción de cuándo usar este agente (usada para auto-detección) |
| `herramientas` | Lista de herramientas disponibles para el agente |
| `modelo` | Modelo AI para utilizar |

---

### Relacionado

- [Referencia de agentes personalizados →](https://kiro.dev/docs/chat/custom-agents/)
- [Autopilot →](./02_Autopilot.md) — Los subagentes funcionan principalmente en modo Autopilot

---

*📂 Capítulo: **Chat > Web tools***

## Herramientas web

![Herramientas web](https://kiro.dev/videos/webtools.mp4)

> **Fuente:** [kiro.dev/docs/chat/webtools/](https://kiro.dev/docs/chat/webtools/)

---

Las herramientas web permiten a Kiro obtener contenido de la web y enriquecer sus respuestas con resultados de búsqueda web.

---

### Descripción general

Con las herramientas web, Kiro puede:

- **Obtener contenido** — Obtener el contenido de una URL específica para usar como contexto
- **Búsqueda web** — Fundamentar respuestas con resultados de búsqueda actuales

Para usar el fetch: pegá una URL en el chat y Kiro la procesará como contexto.

---

### Limitaciones

| Parámetro | Límite |
|---|---|
| **Tamaño máximo por página** | 10MB |
| **Tiempo de espera por solicitud** | 30 segundos |
| **Redirecciones máximas** | 10 |
| **Tipo de contenido** | Solo páginas `text/html` |
| **Reintentos automáticos** | 3 intentos en caso de falla |

---

### Gobernanza

Los clientes del nivel **Pro que usan IAM Identity Center** como método de inicio de sesión pueden controlar el acceso a las herramientas web para los usuarios de su organización.

- Herramientas web están **habilitadas por defecto** en Kiro
- Los administradores pueden deshabilitarlas desde la consola de AWS
- ⚠️ La restricción se aplica en el lado del cliente — los usuarios finales podrían evitarla

---

### Deshabilitar las herramientas web para su organización

1. Ir a la consola de AWS
2. Navegar a la configuración de Amazon Q / Kiro para tu organización
3. Deshabilitar herramientas web para los usuarios del inquilino

---

### Relacionado

- [Privacidad y Seguridad →](../11_Privacidad y seguridad.md)
- [Powers →](../09_Powers.md) — Alternativa para acceder a documentación especializada sin búsqueda web

---

*📂 Capítulo: **Agent Skills***

## Skills del agente

> **Fuente:** [kiro.dev/docs/skills/](https://kiro.dev/docs/skills/)

---

Las skills son paquetes de instrucciones portátiles que siguen el estándar abierto [Agent Skills](https://agentskills.io). Incluyen instrucciones, scripts y plantillas en paquetes reutilizables que Kiro puede activar cuando sea relevante para su tarea.

Kiro admite el estándar Agent Skills, por lo que puedes importar skills de la comunidad u otras herramientas de IA compatibles y compartir tus propias skills en todo el ecosistema.

---

### ¿Qué son las skills?

Las skills resuelven la tensión entre **muy poco contexto** (los agentes adivinan) y **demasiado contexto** (los agentes disminuyen la velocidad) a través de la **divulgación progresiva**:

1. **Descubrimiento**: al inicio, Kiro carga solo el nombre y la descripción de cada skill.
2. **Activación**: cuando tu solicitud coincide con la descripción de una skill, Kiro carga las instrucciones completas.
3. **Ejecución**: Kiro sigue las instrucciones y carga scripts o archivos de referencia solo según sea necesario.

Esto mantiene el contexto enfocado y al mismo tiempo le brinda a Kiro acceso a un amplio conocimiento especializado bajo demanda.

---

### Cómo funcionan las skills

Sin conocimiento del proceso de implementación de su equipo, los estándares de revisión de código de su empresa o el proceso de análisis de datos de su proyecto, los agentes adivinan e iteran, tal como lo haría usted cuando aprende algo nuevo. Cargar todo este contexto por adelantado no es práctico.

Las skills resuelven esto cargando las instrucciones completas de las skills solo cuando Kiro determina que tu solicitud coincide con el propósito de una skill.

---

### Usando skills

Kiro **activa skills automáticamente** cuando tu solicitud coincide con la descripción de una skill.

También puedes invocar una skill directamente: escribe `/` en la entrada del chat para ver las skills disponibles como **comandos de barra diagonal**. Al seleccionar un comando de barra diagonal se cargan las instrucciones de skill completas.

Vea y administre skills en la sección **Steering y skills del agente** en el panel de Kiro.

---

### Alcance de la skill

| Alcance | Ubicación | Mejor para |
|---|---|---|
| **Espacio de trabajo** | `.kiro/skills/` en la raíz del proyecto | Procedimientos de equipo, flujos de trabajo específicos de proyectos |
| **Global** | `~/.kiro/skills/` en el directorio de inicio | Flujos de trabajo personales, hábitos entre proyectos |

---

### Importación de skills

1. Abra la sección **Steering y skills del agente** en el panel de Kiro.
2. Haga clic en **+** y seleccione **Importar una skill**
3. Elige tu fuente:
   - **GitHub** — Importar desde una URL de repositorio público (pegue la URL que apunta a la carpeta de skills o directamente al archivo `SKILL.md`). La URL debe apuntar a un subdirectorio, no a la raíz del repositorio.
   - **Carpeta local** — Importar desde su sistema de archivos

Las skills importadas se copian en su directorio de skills y funcionan inmediatamente.

---

### Creando una skill

Una skill es una carpeta que contiene un archivo `SKILL.md`:

```
my-skill/
├── SKILL.md        # Required
├── scripts/        # Optional executable code
├── references/     # Optional documentation
└── assets/         # Optional templates
```

#### Formato SKILL.md

```markdown
---
nombre: pr-revisión
Descripción: revise las pull requests para determinar la calidad del código, los problemas de seguridad y la cobertura de las pruebas. Úselo al revisar relaciones públicas o preparar código para revisión.
---

### Proceso de revisión

1. Verifique las vulnerabilidades de seguridad
2. Verificar el manejo de errores
3. Confirmar la cobertura de la prueba
4. Revisar el nombre y la estructura.
```

#### Campos frontales

| Campo | Requerido | Descripción |
|---|---|---|
| `nombre` | ✅ | Identificador de skill (usado como comando de barra diagonal) |
| `descripción` | ✅ | Utilizado por Kiro para decidir cuándo activar |
| `licencia` | ✗ | Identificador de licencia SPDX |
| `compatibilidad` | ✗ | Herramientas de IA compatibles |
| `metadatos` | ✗ | Metadatos clave/valor adicionales |

Consulte la [especificación completa →](https://agentskills.io/specification)

---

### En qué se diferencian las skills de la dirección y los poderes

| Característica | Skills | Dirección | Poderes |
|---|---|---|---|
| **Estándar** | Abierto (especificación de skills del agente) | Específico de Kiro | Específico de Kiro |
| **Cargando** | Bajo demanda | siempre/auto/fileMatch/manual | Dinámico basado en el contexto |
| **Guiones** | ✅ Sí | ✗ No | ✅ Sí |
| **Herramientas MCP** | ✗ No | ✗ No | ✅ Sí |
| **Mejor para** | Flujos de trabajo reutilizables para compartir o importar | Estándares y convenciones de proyectos | Integraciones de MCP con conocimientos agrupados |

> Para las integraciones de MCP, [Powers](https://kiro.dev/docs/powers) suelen ser una mejor opción: combinan herramientas con orientación integrada y se activan automáticamente.

---

### Mejores prácticas

- **Escribe descripciones precisas**: Kiro usa la descripción para decidir cuándo activar. Incluya palabras clave específicas: "Revisar las pull requests para seguridad y cobertura de pruebas" supera a "ayuda con la revisión del código".
- **Mantenga enfocado SKILL.md**: coloque documentación detallada en archivos `referencias/`. Kiro carga el `SKILL.md` completo al activarlo.
- **Utilice secuencias de comandos para tareas deterministas**: la validación, la generación de archivos y las llamadas API funcionan mejor como secuencias de comandos que el código generado por LLM.
- **Elija el alcance correcto**: global para flujos de trabajo personales (su lista de verificación de revisión), espacio de trabajo para procedimientos de equipo (implementación de proyectos).

---

### Documentación relacionada

- [Dirección →](https://kiro.dev/docs/steering) — Contexto y estándares específicos del proyecto
- [Poderes →](https://kiro.dev/docs/powers) — Integraciones de MCP con conocimientos incluidos
- [Especificación de skills del agente →](https://agentskills.io/specification)

---

*📂 Capítulo: **Powers > Install powers***

## Instalar poderes

> **Fuente:** [kiro.dev/docs/powers/](https://kiro.dev/docs/powers/) · [kiro.dev/powers](https://kiro.dev/powers)

---

### ¿Qué son los poderes?

Powers son paquetes que combinan **servidores MCP + dirección + hooks**, activados dinámicamente según el contexto de tu conversación. En lugar de cargar todas las herramientas de golpe MCP, los poderes se activan solo cuando son relevantes.

#### El problema: sobrecarga de contexto

| Poderes del pecado | Poderes estafadores |
|---|---|
| Conectar 5 servidores MCP carga más de 100 definiciones de herramientas antes de tu primer aviso | Las herramientas se cargan **on-demand** basado en palabras clave de la conversación |
| 5 servidores pueden consumir 50.000+ tokens (40% de la ventana de contexto) | Solo se carga lo relevante al task actual |
| Sin contexto del framework, el agente adivina | Acceso instantáneo a conocimiento especializado |

#### Cómo funcionan los poderes

Cuando inició una tarea, Kiro:
1. Lee la descripción de la tarea
2. Evalúa los poderes instalados contra el task
3. Carga **solo** los poderes relevantes en contexto

#### ¿Qué hay en un poder?

| Componente | Descripción |
|---|---|
| `PODER.md` | Archivo de Steering que describe al agente qué herramientas MCP tienen disponibles y cuándo usarlas |
| Configuración del servidor MCP | Herramientas y detalles de conexión al servidor MCP |
| Dirección / Hooks | Tareas automatizadas en eventos del IDE o comandos de barra (opcional) |

**Ejemplo:** Instala el Stripe power. Cuando mencionás "pago" o "pago", el power se activa — cargando las herramientas MCP de Stripe y el `POWER.md`. Cuando pases a trabajar con la base de datos, el Supabase power se activa y Stripe se desactiva.

---

### Socios del mercado

Poderes curados de socios oficiales disponibles con un clic:

`Datadog` · `Dynatrace` · `Figma` · `Neon` · `Netlify` · `Postman` · `Supabase` · `Stripe` · `Strands SDK` · `AWS Aurora`

---

### Instalación de una fuente de alimentación

#### Desde Marketplace (un clic)

1. Abrí el panel **Powers** en Kiro
2. Explora los poderes disponibles en [kiro.dev/powers](https://kiro.dev/powers)
3. Haz clic en **Instalar** — el poder se registra automáticamente
4. No requiere configuración manual de JSON ni configuración por línea de comandos

#### De GitHub

1. Abrí el panel **Powers** en Kiro
2. Seleccioná **Añadir potencia desde GitHub**
3. Pegá la URL del repositorio público del power
4. Kiro descarga e instala el poder automáticamente

#### Desde la ruta local

1. Abrí el panel **Powers** en Kiro
2. Seleccioná **Agregar energía desde la ruta local**
3. Selecciona el directorio de tu power local
4. Ideal para testear poderes propios antes de publicarlos

---

### Próximos pasos

- [Crea tu propio poder →](./02_Create powers.md)
- [Explorar el mercado →](https://kiro.dev/powers)

---

*📂 Capítulo: **Powers > Create powers***

## Crear poderes

> **Fuente:** [kiro.dev/docs/powers/create/](https://kiro.dev/docs/powers/create/)

---

Crea tus propios poderes para extender las capacidades de Kiro con herramientas especializadas, y compartílos con la comunidad.

---

### Lo que necesitas

Todo poder necesita un archivo `POWER.md`. Opcionalmente podés agregar:

- `mcp.json` — Configuración de servidores MCP para integraciones de herramientas
- `steering/` — Archivos de guía específicos por flujo de trabajo

---

### Creando POWER.md

El archivo `POWER.md` tiene dos partes: **frontmatter** e **instrucciones para el agente**.

#### Frontmatter: Cuándo activar

El frontmatter le dice a Kiro cuándo cargar tu poder. Usá palabras clave que coinciden con cómo los desarrolladores hablan de tu herramienta.

```yaml
---
name: "supabase"
displayName: "Supabase with local CLI"
description: "Build fullstack applications with Supabase's Postgres database, authentication, storage, and real-time subscriptions"
keywords: ["database", "postgres", "auth", "storage", "realtime", "backend", "supabase", "rls"]
---
```

**Cómo funciona:** Cuando alguien dice "Configuremos la base de datos", Kiro ve "database" en los palabras clave y activa el poder de Supabase. Los MCP tools y la documentación del power se cargan automáticamente en contexto.

#### Instrucciones de incorporación

La sección de onboarding corre cuando alguien usa tu poder por primera vez. Usala para validar dependencias, explicar pasos de configuración o crear hooks de espacio de trabajo.

```markdown
## Incorporación

### Paso 1: Validar el funcionamiento de las herramientas
Antes de usar Supabase Local MCP, asegúrese de que esté instalado lo siguiente:
- **Docker Desktop**: Verificar con: `docker --version`
  - **CRÍTICO**: Si Docker no está instalado o no se está ejecutando, NO continúe.
- **Supabase CLI**: Verificar con: `supabase --version`

### Paso 2: agregar hooks
Agregue un gancho a `.kiro/hooks/review-advisors.kiro.hook`
```

Kiro sigue estas instrucciones automáticamente: verifica que Docker esté corriendo, valida la CLI e instala el gancho de revisión en el espacio de trabajo.

#### Instrucciones de dirección

**Enfoque simple** (sin archivos de Steering separados): Incluye toda la guía directamente en `POWER.md` después de la sección de incorporación.

**Enfoque avanzado** (múltiples Steering Files): Para herramientas con muchos flujos de trabajo distintos, mapeá cada flujo de trabajo a un archivo de Steering específico:

```markdown
## When to Load Steering Files
- Setting up a database → `database-setup-workflow.md`
- Writing or formatting SQL code → `supabase-code-format-sql.md`
- Creating or modifying RLS policies → `supabase-database-rls-policies.md`
- Creating PostgreSQL functions → `supabase-database-functions.md`
- Setting up Next.js auth with Supabase SSR → `supabase-nextjs-supabase-auth.md`
- Implementing realtime features → `supabase-use-realtime.md`
```

Esto previene sobrecargar el contexto con todos los patrones de golpe — Kiro carga solo el manejo relevante al flujo de trabajo actual.

---

### Agregar servidores MCP

Si utilizas herramientas MCP, creará un archivo `mcp.json`. Los nombres de servidores deben coincidir con los referenciados en `POWER.md`.

```json
{
  "mcpServers": {
    "supabase-local": {
      "command": "npx",
      "args": ["-y", "@supabase/mcp-server-supabase"],
      "env": {
        "SUPABASE_URL": "${SUPABASE_URL}",
        "SUPABASE_ANON_KEY": "${SUPABASE_ANON_KEY}"
      }
    }
  }
}
```

> ⚠️ Usamos variables de entorno para claves y secretos API. Durante la instalación, Kiro automáticamente asigna espacios de nombres a los nombres del servidor para evitar conflictos (ej. `supabase-local` → `power-supabase-supabase-local`).

---

### Estructura del directorio

```
power-supabase/
├── POWER.md          # Metadata, onboarding, steering mappings
├── mcp.json          # MCP server configuration
└── steering/         # Workflow-specific guidance
    ├── database-setup-workflow.md
    ├── supabase-code-format-sql.md
    ├── supabase-database-rls-policies.md
    └── supabase-edge-functions.md
```

---

### Ejemplos

| Tipo | Estructura |
|---|---|
| **Simple** (archivos de Steering sin) | `POWER.md` + `mcp.json` (opcional) |
| **Con dirección de herramienta única** | `POWER.md` + `mcp.json` + `dirección/schema-patterns.md` |
| **Multiherramienta** | `POWER.md` + `mcp.json` + Múltiples archivos en `steering/` |
| **Solo documentación** | `POWER.md` + `steering/` (sin servidores MCP) |

---

### Pruebas localmente

1. Cree el directorio del power con los archivos necesarios
2. Abrí **Kiro → Panel de poderes → Agregar energía desde la ruta local**
3. Selecciona tu directorio del poder
4. Testeá la activación usando palabras clave de tu power en una conversación

---

### Compartiendo tu poder

Publicá tu power en un repositorio público de GitHub:

```bash
git init
git add POWER.md mcp.json steering/
git commit -m "Initial release"
git push origin main
```

> El repositorio debe ser **público** para que otros puedan instalarlo. Los repositorios privados requieren que los usuarios tengan permisos de acceso.

Otros pueden instalarlo vía **Add power from GitHub** usando la URL de tu repositorio.

---

*📂 Capítulo: **Hooks > Hook triggers***

## Hooks

> **Fuente:** [kiro.dev/docs/hooks/](https://kiro.dev/docs/hooks/)

---

Los enlaces de agente son activadores automatizados que ejecutan mensajes de agente predefinidos o comandos de shell cuando ocurren eventos específicos en su IDE. En lugar de solicitar manualmente tareas rutinarias, los hooks configuran respuestas automáticas a los eventos.

---

### ¿Qué son los hooks de agentes?

![Kiro Gancho](https://kiro.dev/videos/kiro-hook.mp4)

Los hooks pueden activarse en:
- Guardar, crear o eliminar archivos
- Envío de avisos del usuario y finalización del turno del agente.
- Antes o después de las invocaciones de herramientas.
- Antes o después de la ejecución de la tarea especificada
- Disparadores manuales bajo demanda

**Beneficios de los hooks de agentes:**
- Mantener una calidad de código consistente automáticamente
- Prevenir vulnerabilidades de seguridad.
- Reducir los gastos generales manuales
- Estandarizar los procesos del equipo.
- Crear ciclos de desarrollo más rápidos

---

### Cómo funcionan los hooks de agentes

El sistema de enlace de agente sigue un proceso simple de dos pasos:

1. **Detección de eventos**: el sistema monitorea eventos específicos en su IDE
2. **Acción automatizada**: cuando ocurre un evento, se ejecuta una acción (solicitud de agente o comando de shell)

---

### Configuración de enlaces de agentes

#### Creando un gancho

1. Navegue a la sección **Agent Hooks** en el panel de Kiro.
2. Haga clic en el botón **+** para crear un nuevo gancho.
3. Elige cómo quieres crear el gancho:
   - **Crear un gancho manualmente**: configure un gancho a mano en un formulario
   - **Pídele a Kiro que cree un gancho**: describe un gancho usando lenguaje natural.

También puede abrir la interfaz de usuario de Hook desde la paleta de comandos:
- macOS: `Cmd + Shift + P` → `Kiro: abrir la interfaz de usuario de Kiro Hook`
- Windows/Linux: `Ctrl + Shift + P` → `Kiro: abrir la interfaz de usuario de Kiro Hook`

---

#### Pídele a Kiro que cree un gancho

1. Selecciona **Pedirle a Kiro que cree un gancho**
2. Describe el flujo de trabajo del gancho en lenguaje natural.
3. Presione Entrar o haga clic en **Enviar**
4. Revise la configuración generada, ajústela si es necesario y haga clic en **Guardar enlace**

---

#### Crear un gancho manualmente

1. Seleccione **Crear un enlace manualmente** para abrir el formulario del enlace.
2. Complete los campos del formulario:

| Campo | Descripción |
|---|---|
| **Título** | Un nombre corto para el anzuelo |
| **Descripción** | Qué hace el anzuelo |
| **Evento** | El tipo de activador (p. ej., Guardar archivo, Uso posterior de la herramienta, Ejecución previa a la tarea) |
| **Nombre de la herramienta** | Para hooks de uso previo/posterior a la herramienta, especifique qué herramientas deben coincidir |
| **Patrón de archivo** | Para enlaces de eventos de archivos, especifique qué archivos deben coincidir (por ejemplo, `src/**/*.tsx`) |
| **Acción** | Elija **Preguntar a Kiro** (solicitud de agente) o **Ejecutar comando** (comando de shell) |
| **Instrucciones o Comando** | El símbolo del sistema o comando de shell para ejecutar |

3. Haga clic en **Crear gancho** cuando haya terminado, o en **Borrar** para restablecer el formulario.

---

### Próximos pasos

- [Disparadores de gancho →](https://kiro.dev/docs/hooks/hook-triggers/)
- [Acciones de gancho →](https://kiro.dev/docs/hooks/hook-actions/)
- [Ejemplos →](https://kiro.dev/docs/hooks/examples/)
- [Gestión →](https://kiro.dev/docs/hooks/management/)
- [Mejores prácticas →](https://kiro.dev/docs/hooks/best-practices/)
- [Solución de problemas →](https://kiro.dev/docs/hooks/troubleshooting/)

---

*📂 Capítulo: **Hooks > Hook actions***

## Acciones de gancho

> **Fuente:** [kiro.dev/docs/hooks/actions/](https://kiro.dev/docs/hooks/actions/)

---

Cada gancho puede ejecutar uno de dos tipos de acciones cuando su disparador se activa.

---

### Acción de solicitud del agente

Defina un mensaje que se envía al agente cada vez que el gancho se dispara. El agente responde y actúa sobre ese aviso igual que con un aviso enviado desde el panel de chat.

**Caso especial — PromptSubmit:** La acción se llama "Agregar al mensaje". El aviso del gancho se **agrega** al aviso del usuario, y el combinado se envía al agente.

**Cuándo usarlo:**
- Cuando quieras usar lenguaje natural para instruir al agente a realizar alguna acción basada en contexto
- Para tareas que requieren razonamiento o evaluación inteligente
- Cuando la salida depende del contexto actual del agente

> ⚠️ Las acciones de Agent Prompt **consumen créditos** ya que disparan un nuevo agente loop.

---

### Acción del comando Shell

Defina un comando de shell que se ejecute cada vez que el gancho se dispare.

| Resultado del comando | Comportamiento |
|---|---|
| Código de salida `0` (éxito) | El stdout se agrega al contexto del agente |
| Cualquier otro código de salida | El stderr se envía al agente con notificación de error |
| Herramienta previa Uso gancho + error | La invocación de la herramienta es **bloqueada** |
| Preguntar Enviar gancho + error | El envío del aviso es **bloqueado** |

**Tiempo de espera:** Configurable por gancho. El valor predeterminado es **60 segundos**. Seteá `0` para deshabilitar el tiempo de espera.

**Cuándo usarlo:**
- Cuando quieras ejecutar comandos específicos o acciones determinísticas
- Para tareas que no dependen del contexto actual del agente
- Para scripts de validación, linting, formateo, etc.

> ✅ Las acciones de Shell Command son **más rápidas** que las acciones de Agent Prompt y **no consumen créditos**, ya que se ejecutan localmente.

---

### Seleccionar un tipo de acción

| Criterio | Aviso del agente | Comando Shell |
|---|---|---|
| Basado en contexto | ✅ | ❌ |
| Lenguaje natural | ✅ | ❌ |
| Determinístico | ❌ | ✅ |
| Consumir créditos | ✅ | ❌ |
| Velocidad | Más lento (LLM) | Más rápido (local) |
| Ideal para | Revisión, análisis, generación | Linting, formateo, scripts |

---

*📂 Capítulo: **Hooks > Examples***

## Ejemplos de hooks

> **Fuente:** [kiro.dev/docs/hooks/examples/](https://kiro.dev/docs/hooks/examples/)

---

Ejemplos prácticos y plantillas listas para usar en tus proyectos.

---

### Escáner de commit previa de seguridad

Previene fugas de seguridad escaneando archivos antes de ser comprometidos.

| Campo | Valor |
|---|---|
| **Disparador** | Parada del agente |
| **Acción** | Aviso del agente |

**Aviso:**
```
Revise los archivos modificados para detectar posibles problemas de seguridad:
1. Busque claves, tokens o credenciales de API en el código fuente
2. Verifique claves privadas o credenciales confidenciales
3. Busque claves o certificados de cifrado
4. Identificar tokens de autenticación o ID de sesión
5. Marcar contraseñas o secretos en archivos de configuración
6. Detectar direcciones IP que contengan datos confidenciales
7. Encuentre URL internas codificadas
8. Detectar las credenciales de conexión a la base de datos

Para cada problema encontrado:
1. Resalte el riesgo de seguridad específico
2. Sugerir un enfoque alternativo seguro
3. Recomendar mejores prácticas de seguridad
```

---

### Registro centralizado de mensajes de usuario

Loguea todos los avisos de usuario a un sistema centralizado para análisis y auditoría.

| Campo | Valor |
|---|---|
| **Disparador** | Envío rápido |
| **Acción** | Comando Shell |

**Comando:**
```golpecito
## Registrar mensaje de usuario en Grafana Loki
curl -H "Tipo de contenido: aplicación/json" -XPOST \
  "http://loghost/loki/api/v1/push" --data-raw\
  "{'streams': [{ 'stream': { 'app': 'kiro', 'user': \"${USER}\" }, 'values': [ [\"$(date +%s%N)\", \"${USER_PROMPT}\"] ] }]}"
```

---

### Ayudante de Internacionalización

Mantiene las traducciones sincronizadas cuando se actualiza el archivo del idioma principal.

| Campo | Valor |
|---|---|
| **Disparador** | Guardar archivo |
| **Objetivo** | `src/locales/en/*.json` |
| **Acción** | Aviso del agente |

**Aviso:**
```
Cuando se actualiza un archivo local en inglés:
1. Identifique qué claves de cadena se agregaron o modificaron
2. Verifique todos los archivos de otros idiomas para estas claves.
3. Si faltan claves, agréguelas con un marcador "NEEDS_TRANSLATION".
4. Para claves modificadas, márquelas como "NEEDS_REVIEW"
5. Genere un resumen de los cambios necesarios en todos los idiomas.
```

---

### Mantenedor de cobertura de prueba

Asegúrese de que la cobertura de pruebas se mantenga alta a medida que el código evolucione.

| Campo | Valor |
|---|---|
| **Disparador** | Guardar archivo |
| **Objetivo** | `src/**/*.{js,ts,jsx,tsx}` |
| **Acción** | Aviso del agente |

**Aviso:**
```
Cuando se modifica un archivo fuente:
1. Identificar funciones y métodos nuevos o modificados.
2. Verificar si existen pruebas correspondientes y cubrir los cambios.
3. Si falta cobertura, genere casos de prueba para el nuevo código.
4. Ejecute las pruebas para verificar que pasen.
5. Actualizar informes de cobertura
```

---

### Generador de documentación

Genera documentación completa bajo demanda para el archivo actual.

| Campo | Valor |
|---|---|
| **Disparador** | manuales |
| **Acción** | Aviso del agente |

**Aviso:**
```
Genere documentación completa para el archivo actual:
1. Extraer firmas de funciones y clases
2. Parámetros del documento y tipos de devolución.
3. Proporcionar ejemplos de uso basados en el código existente.
4. Actualice README.md con cualquier exportación nueva.
5. Asegúrese de que la documentación siga los estándares del proyecto.
```

---

### Integración con MCP

Los hooks pueden potenciarse con MCP para acceder a herramientas externas especializadas.

**Cómo usar MCP con hooks:**
1. [Configurar servidores MCP →](../13_MCP/01_Configuration.md)
2. Referenciar las herramientas MCP en las instrucciones del gancho
3. Configurar `autoApprove` para herramientas de uso frecuente

**Casos de uso:**
- Verifica que tu sistema de diseño Figma sea respetado
- Actualizar el estado de un ticket después de completar una tarea
- Sincronizar una base de datos desde archivos del proyecto

---

*📂 Capítulo: **Hooks > Management***

## Gestión de hooks

> **Fuente:** [kiro.dev/docs/hooks/management/](https://kiro.dev/docs/hooks/management/)

---

Accedé a todos tus hooks desde la sección **Agent Hooks** en el panel de Kiro.

---

### Activar/Desactivar hooks

Activa o desactiva los hooks sin eliminarlos:

| Método | Cómo |
|---|---|
| **Alternancia rápida** | Haga clic en el ícono de ojo (👁) junto al gancho en el panel |
| **Desde la vista del gancho** | Seleccione el gancho → cambiar **Hook Enabled** en la esquina superior derecha |

---

### Editar hooks existentes

Los hooks evolucionan con tu flujo de trabajo. Actualizalos en cualquier momento:

1. Selecciona el gancho en el panel **Agent Hooks**
2. Modificá los campos: disparador, patrones de archivo, instrucciones o descripción
3. Los cambios se aplican **inmediatamente**

---

### Eliminar hooks

1. Selecciona el gancho en el panel **Agent Hooks**
2. Haga clic en **Eliminar gancho** (parte inferior de la vista)
3. Confirmá haciendo clic en **Eliminar**

> ⚠️ Esta acción **no se puede deshacer**.

---

### Ejecutar hooks de gatillo manual

Para hooks con gatillo de tipo **Manual**:

| Método | Cómo |
|---|---|
| **Ejecución rápida** | Click en el botón ▷ junto al nombre del gancho en el panel |
| **Desde la vista del gancho** | Seleccione el gancho → haga clic en **Iniciar gancho** en la esquina superior derecha |

---

### Almacenamiento de gancho

Los hooks se almacenan como archivos JSON en:

- `.kiro/hooks/` — engancha un espacio de trabajo nivelado (compartidos con el equipo vía git)
- Los hooks a nivel del espacio de trabajo son visibles para todos los colaboradores del proyecto.

---

*📂 Capítulo: **Hooks > Best practices***

## Mejores prácticas de gancho

> **Fuente:** [kiro.dev/docs/hooks/best-practices/](https://kiro.dev/docs/hooks/best-practices/)

---

### Diseño de gancho

#### Sea específico y claro
- Escribí instrucciones detalladas y sin ambigüedad para el agente
- Enfocá cada gancho en **una sola tarea específica**
- Usa pasos numerados para operaciones complejas

#### Pruebe a fondo
- Testeá hooks con escenarios de ejemplo antes de usarlos en producción
- Verifica que funcionan con casos extremos
- Para hooks relacionados con archivos, empezá con patrones de archivos limitados antes de expandir

#### Supervisar el rendimiento
- Asegurate de que los hooks no ralenticen tu flujo de trabajo
- Considerá la frecuencia de los eventos desencadenantes
- Optimizá los indicadores de eficiencia.

---

### Consideraciones de seguridad

#### Validar entradas
- Asegurate de que los hooks manejen contenido inesperado con gracia
- Considerará posibles casos extremos
- Testeá con entrada malformada o inesperada

#### Limitar el alcance
- Para hooks relacionados con archivos, puntúe a tipos de archivo o directorios específicos cuando sea posible
- Usá patrones de archivos precisos para evitar ejecuciones innecesarias
- Considerará el impacto de los hooks en todo el código base.

#### Revisar periódicamente
- Actualizá la lógica del gancho a medida que el proyecto evoluciona
- Elimina los hooks que ya no sean necesarios
- Refina los avisos basándote en los resultados reales

---

### Colaboración en equipo

#### Hooks para documentos
- Mantené documentación clara del propósito de cada gancho.
- Incluye ejemplos del comportamiento esperado.
- Documentación de limitaciones de casos extremos

#### Compartir configuraciones
- Usá hooks consistentes entre todos los miembros del equipo
- Almacená las configuraciones de hooks en control de versiones (`.kiro/hooks/`)
- Crea hooks estándar para flujos de trabajo comunes del equipo

#### Integración del control de versiones
- Considerá hooks que se integran con tu sistema de control de versiones
- Crea hooks para flujos de trabajo de revisión de código.
- Usá hooks para hacer cumplir los estándares del equipo

---

### Referencia rápida: Shell frente a indicador del agente

| Situación | Usar |
|---|---|
| Linting, formato, scripts determinísticos | **Comando Shell** (más rápido, sin créditos) |
| Revisión, análisis, generación de contenido | **Agent Prompt** (contextual, consumir créditos) |
| Validación precompromiso | **Comando Shell** |
| Sugerencias de código | **Aviso del agente** |

---

*📂 Capítulo: **Hooks > Troubleshooting***

## Hooks de solución de problemas

> **Fuente:** [kiro.dev/docs/hooks/troubleshooting/](https://kiro.dev/docs/hooks/troubleshooting/)

---

### Problemas comunes

#### El gancho no se activa

| Posible causa | Solución |
|---|---|
| El patrón del archivo no coincide | Verificá que el patrón coincide con los archivos objetivo |
| Gancho deshabilitado | Verifique que el gancho esté habilitado (ícono de ojo en el panel) |
| Tipo de evento incorrecto | Revisa que el Evento seleccionado sea el correcto para tu caso |

#### Comportamiento inesperado del gancho

| Posible causa | Solución |
|---|---|
| Instrucciones ambiguas | Revisá las instrucciones del gancho para mayor claridad |
| Hooks en conflicto | Verificá si hay otros hooks que se disparan en el mismo evento |
| Patrones de archivos demasiado amplios | Acotá los patrones a archivos más específicos |

#### Problemas de rendimiento

| Posible causa | Solución |
|---|---|
| Patrones de archivos muy amplios | Usamos patrones más específicos para reducir el alcance |
| Instrucciones complejas (Agent Prompt) | Simplificá las instrucciones del gancho |
| Comando lento (Comando Shell) | Asegurate de que el comando se complete rápidamente |
| Demasiados desencadenan acontecimientos | Reduzca la frecuencia de los eventos de disparo |

---

### Consejos de depuración

1. **Verificá el tipo de trigger** — Confirmá que el tipo de evento coincide con cuando esperes que corra el gancho
2. **Testeá el patrón de archivo** — Utilice un patrón más amplio temporalmente para verificar que el gancho se activa
3. **Revisá el panel de Output** — Buscá errores o mensajes de los hooks en ejecución
4. **Simplificá primero** — Empezá con un gancho simple, confirma que funciona, y luego agrega complejidad

---

### Relacionado

- Para problemas más generales, consulte la [guía de solución de problemas principal →](../12_Troubleshooting.md)
- [Mejores prácticas →](./05_Best%20practices.md)
- [Gestión de hooks →](./04_Management.md)

---

*📂 Capítulo: **Steering***

## Steering

> **Fuente:** [kiro.dev/docs/steering/](https://kiro.dev/docs/steering/)

---

Los archivos de Steering guían la IA de Kiro con un contexto global o específico del espacio de trabajo a través de documentos Markdown que definen sus estándares, arquitectura y convenciones, lo que le brinda a Kiro una comprensión persistente de cómo funciona su proyecto.

---

### ¿Qué es el Steering?

Los archivos de Steering son documentos Markdown almacenados en `.kiro/steering/` que Kiro lee automáticamente durante las interacciones de chat. Proporcionan conocimiento específico del proyecto que da forma a las sugerencias, la generación de código y el comportamiento de Kiro.

**Beneficios clave:**
- Mantener una calidad de código consistente en todas las sesiones.
- Compartir convenciones de equipo automáticamente
- Reducir las correcciones repetitivas
- Habilitar experiencia en un dominio específico

---

### Alcance del archivo de Steering

#### Steering del espacio de trabajo

Reside en `.kiro/steering/` en la raíz de tu espacio de trabajo. Aplicar solo a ese espacio de trabajo específico. Se utiliza para informar a Kiro sobre patrones, bibliotecas y estándares que se aplican a un espacio de trabajo individual.

#### Steering global

Reside en `~/.kiro/steering/` en tu directorio de inicio. Aplicar a **todos** los espacios de trabajo. Se utiliza para informar a Kiro sobre las convenciones que se aplican en todos sus proyectos.

> **Nota:** En caso de instrucciones contradictorias entre el Steering global y del espacio de trabajo, **el Steering del espacio de trabajo tiene prioridad**.

#### Steering del equipo

El Steering global puede distribuir archivos de Steering centralizados a equipos completos a través de soluciones MDM, políticas de grupo o descargándolos desde un repositorio central a `~/.kiro/steering`.

---

### Archivos de Steering fundamentales

Haga clic en **Generar documentos de Steering** en el panel de Kiro para generar automáticamente tres archivos fundamentales:

| Archivo | Propósito |
|---|---|
| `producto.md` | Define el propósito de su producto, los usuarios objetivo, las características clave y los objetivos comerciales.
| `tecnología.md` | Marcos de documentos, bibliotecas, herramientas de desarrollo y limitaciones técnicas |
| `estructura.md` | Describe la organización de archivos, convenciones de nomenclatura, patrones de importación y decisiones arquitectónicas |

Estos archivos básicos se incluyen en cada interacción de forma predeterminada.

---

### Creación de archivos de Steering personalizados

1. Navegue a la sección **Steering** en el panel Kiro.
2. Haga clic en el botón **+**
3. Seleccione el alcance: **espacio de trabajo** o **global**
4. Elija un nombre de archivo descriptivo (por ejemplo, `api-standards.md`)
5. Escriba su guía utilizando Markdown estándar y lenguaje natural.
6. Opcionalmente, utilice el botón **Refinar** para que Kiro mejore sus requisitos.

---

### Agentes.md

Kiro admite el estándar [AGENTS.md](https://agents.md/). Agregue archivos `AGENTS.md` a `~/.kiro/steering/` o a la carpeta raíz de su espacio de trabajo.

> **Nota:** Los archivos AGENTS.md están **siempre incluidos** y no admiten modos de inclusión.

---

### Modos de inclusión

Configure cuándo se cargan los archivos de Steering agregando el texto preliminar de YAML en la parte superior del archivo:

#### Siempre incluido (predeterminado)
```yaml
---
inclusión: siempre
---
```
Cargado en cada interacción de Kiro. Ideal para: pila de tecnología, convenciones de codificación, políticas de seguridad.

#### Inclusión condicional
```yaml
---
inclusión: fileMatch
fileMatchPattern: "componentes/**/*.tsx"
---
```
Se incluye solo cuando se trabaja con archivos que coinciden con el patrón. Múltiples patrones:
```yaml
---
inclusión: fileMatch
fileMatchPattern: ["**/*.ts", "**/*.tsx", "**/tsconfig.*.json"]
---
```
Ideal para: patrones de componentes, reglas de diseño de API, enfoques de prueba específicos para ciertos tipos de archivos.

#### Inclusión manual
```yaml
---
inclusión: manual
---
```
Incluya bajo demanda haciendo referencia con `#steering-file-name` en el chat o mediante comandos de barra diagonal `/`. Ideal para: guías de solución de problemas, procedimientos de migración o documentación con mucho contexto.

#### Inclusión automática
```yaml
---
inclusión: automático
nombre: api-diseño
Descripción: Patrones y convenciones de diseño de API REST. Úselo al crear o modificar puntos finales de API.
---
```
Se incluye automáticamente cuando su solicitud coincide con la descripción. También disponible como comandos de barra diagonal. Ideal para: orientación con mucho contexto que solo debe cargarse cuando sea relevante.

---

### Referencias de archivos

Enlace a archivos del espacio de trabajo en vivo para mantener el Steering actualizado:
```
##[[archivo:<nombre_archivo_relativo>]]
```

Ejemplos:
- `#[[archivo:api/openapi.yaml]]`
- `#[[archivo:componentes/ui/button.tsx]]`
- `#[[archivo:.env.ejemplo]]`

---

### Mejores prácticas

- **Mantenga los archivos enfocados**: un dominio por archivo (diseño, prueba e implementación de API)
- **Utilice nombres claros**: `api-rest-conventions.md`, `testing-unit-patterns.md`
- **Incluir contexto**: explique *por qué* se tomaron decisiones, no solo cuáles son los estándares.
- **Proporcione ejemplos**: use fragmentos de código y comparaciones antes/después
- **La seguridad es lo primero**: nunca incluya claves API, contraseñas ni datos confidenciales
- **Mantener periódicamente**: revisar durante la planificación del sprint y los cambios de arquitectura; Trate los cambios de Steering como cambios de código.

---

### Estrategias comunes de archivos de Steering

| Archivo | Contenido |
|---|---|
| `api-estándares.md` | Convenciones REST, formatos de respuesta de error, flujos de autenticación, estrategias de control de versiones |
| `testing-standards.md` | Patrones de pruebas unitarias, estrategias de integración, burlas, expectativas de cobertura |
| `código-convenciones.md` | Patrones de nombres, organización de archivos, ordenamiento de importaciones, decisiones arquitectónicas |
| `políticas-de-seguridad.md` | Requisitos de autenticación, validación de datos, desinfección de entradas, prevención de vulnerabilidades |
| `despliegue-flujo de trabajo.md` | Procedimientos de compilación, configuraciones del entorno, detalles de la canalización de CI/CD |

---

*📂 Capítulo: **Agent Skills***

## Skills del agente

> **Fuente:** [kiro.dev/docs/skills/](https://kiro.dev/docs/skills/)

---

### ¿Qué son las skills?

Las **Skills** son paquetes de instrucciones portátiles que siguen el estándar abierto [Agent Skills](https://agentskills.io). Agrupan instrucciones, scripts y plantillas en paquetes reutilizables que Kiro puede activar cuando son relevantes para tu tarea.

Kiro soporta el estándar Agent Skills, por lo que podés:
- Importar skills de la comunidad o de otras herramientas de IA compatibles
- Comparte tus propias skills en el ecosistema.

---

### Cómo funcionan las skills

Las skills resuelven el problema del contexto excesivo usando **divulgación progresiva**:

| Etapa | Descripción |
|---|---|
| **1. Descubrimiento** | Al inicio, Kiro carga solo el nombre y descripción de cada skill |
| **2. Activación** | Cuando tu solicitud coincide con la descripción de una skill, Kiro carga las instrucciones completas |
| **3. Ejecución** | Kiro sigue las instrucciones, cargando scripts o archivos de referencia solo cuando es necesario |

Esto mantiene el contexto enfocado mientras da a Kiro acceso a conocimiento especializado extenso bajo demanda.

---

### Usando skills

Kiro activa automáticamente las skills cuando tu solicitud coincide con su descripción.

También podés invocar una skill directamente:
- Escribí `/` en el chat → las skills disponibles aparecen como comandos de barra diagonal
- Seleccioná un comando de barra diagonal → carga las instrucciones completas del Skill

Gestioná tus skills desde la sección **Steering y skills del agente** en el panel de Kiro.

---

### Alcance de la skill

| Alcance | Ubicación | Uso |
|---|---|---|
| **Espacio de trabajo** | `.kiro/skills/` | Solo el proyecto actual. Skills para flujos de trabajo específicos del proyecto (implementación, convenciones del equipo) |
| **Global** | `~/.kiro/skills/` | Disponible en todos los espacios de trabajo. Skills personales utilizadas en cualquier proyecto (revisión de código, documentación) |

> En caso de conflicto de nombres entre skills global y workspace, Kiro **prioriza el workspace skills**. Esto permite definir skills globales con posibilidad de sobreescribirlas por proyecto.

---

### Importación de skills

1. Abra la sección **Steering y skills del agente** en el panel de Kiro
2. Haga clic en **+** y seleccione **Importar una skill**
3. Elegí el origen:
   - **GitHub** — Importará desde una URL de repositorio público (apuntando a la carpeta del Skill o directamente al `SKILL.md`). La URL debe apuntar a un subdirectorio, no a la raíz del repositorio.
   - **Carpeta local** — Importá desde tu sistema de archivos

> Los skills importados se copian a tu directorio de skills y funcionan de inmediato.

---

### Creando una skill

Una skill es una carpeta que contiene un archivo `SKILL.md`:

```
my-skill/
├── SKILL.md          # Requerido
├── scripts/          # Opcional — código ejecutable
├── references/       # Opcional — documentación
└── assets/           # Opcional — templates
```

#### Formato SKILL.md

```markdown
---
nombre: pr-revisión
Descripción: revise las pull requests para determinar la calidad del código, los problemas de seguridad y la cobertura de las pruebas.
             Úselo al revisar relaciones públicas o preparar código para revisión.
---

### Proceso de revisión
1. Verifique las vulnerabilidades de seguridad
2. Verificar el manejo de errores
3. Confirmar la cobertura de la prueba
4. Revisar el nombre y la estructura.
```

#### Campos frontales

| Campo | Descripción |
|---|---|
| `nombre` | Identificador del Skill (usado como comando de barra diagonal) |
| `descripción` | Cuándo activar la skill — debe ser precisa y específica |
| `licencia` | Licencia del Skill (para distribución) |
| `compatibilidad` | Herramientas compatibles con IA |
| `metadatos` | Metadatos adicionales |

Ver la [especificación completa →](https://agentskills.io/specification)

---

### En qué se diferencian las skills de la dirección y los poderes

| Característica | Skills | Dirección | Poderes |
|---|---|---|---|
| **Portabilidad** | ✅ Estándar abierto, compatibles | ❌ Específico de Kiro | ❌ Específico de Kiro |
| **Activación** | Bajo demanda (por descripción / comando de barra diagonal) | Siempre, automático, fileMatch, manual | Dinámica por contexto |
| **Guiones** | ✅ Puede incluir scripts ejecutables | ❌ No | Vía herramientas MCP |
| **Uso ideal** | Flujos de trabajo reutilizables para compartir | Convenciones y estándares del proyecto | Integraciones con herramientas + conocimiento |

> 💡 Para integraciones MCP, los **Powers** suelen ser la mejor opción — incluyen herramientas con guía integrada y se activan automáticamente.

---

### Mejores prácticas

- **Descripciones precisas** — Kiro las usa para decidir cuándo activar. Incluye palabras clave específicas: `"Revisar pull requests para seguridad y cobertura de pruebas"` > `"ayuda con la revisión del código"`
- **SKILL.md enfocado** — Poné documentación detallada en archivos `references/`. Kiro carga el SKILL.md completo en la activación
- **Scripts para tareas determinísticas** — Validación, generación de archivos y llamadas a APIs funcionan mejor como scripts que como código generado por LLM
- **Elegí el alcance correcto** — Global para flujos de trabajo personales; espacio de trabajo para procedimientos del equipo

---

### Relacionado

- [Dirección →](./03_Steering.md)
- [Poderes →](./06_Powers/01_Install%20powers.md)
- [Especificación de skills del agente →](https://agentskills.io/specification)

---

*📂 Capítulo: **Powers***

## poderes

> **Fuente:** [kiro.dev/docs/powers/](https://kiro.dev/docs/powers/)

---

Los poderes son paquetes dinámicos de contexto y herramientas MCP que le brindan a su agente de IA experiencia instantánea para cualquier marco o herramienta, cargando solo lo que es relevante, solo cuando es necesario.

---

### Empezar

- [Explorar poderes](https://kiro.dev/powers): explore poderes seleccionados de socios de lanzamiento e instálelos con un solo clic
- [Instalar un poder →](https://kiro.dev/docs/powers/installation/)
- [Crear un poder →](https://kiro.dev/docs/powers/create/)

---

### Concepto

#### El problema: sobrecarga de contexto

Los agentes de IA se enfrentan a dos desafíos opuestos:

**Sin contexto marco, los agentes suponen.**
Su agente puede llamar a las API de Stripe, pero ¿sabe utilizar claves idempotentes? Puede consultar Neon, pero ¿comprende la agrupación de conexiones sin servidor? Sin experiencia incorporada, usted debe leer la documentación manualmente y refinar los enfoques hasta que el resultado sea el correcto.

**Con demasiado contexto, los agentes se ralentizan.**
Conecte cinco servidores MCP y su agente cargará más de 100 definiciones de herramientas antes de escribir una sola línea de código. Cinco servidores pueden consumir más de 50 000 tokens (el 40 % de su ventana de contexto) antes de su primer mensaje. Más herramientas deberían significar mejores resultados, pero el contexto no estructurado abruma al agente, lo que genera respuestas más lentas y resultados de menor calidad.

---

#### Cómo funcionan los poderes

En lugar de cargar todas las herramientas MCP a la vez, los poderes **se activan dinámicamente según las palabras clave** en su conversación.

Cuando comienzas una tarea, Kiro:
1. Lee la descripción de la tarea.
2. Evalúa las potencias instaladas frente a la tarea
3. Carga **solo poderes relevantes** en contexto

Cuando mencionas "pago" o "pago", el poder de Stripe se activa, cargando las herramientas MCP de Stripe y la dirección POWER.md en contexto. Cuando pasas al trabajo de la base de datos, el poder de Supabase se activa y Stripe se desactiva.

---

#### ¿Qué hay en un poder?

Un poder es un paquete unificado que incluye:

| Componente | Descripción |
|---|---|
| `PODER.md` | Archivo de Steering que le indica al agente qué herramientas MCP tiene disponibles y cuándo usarlas |
| **Configuración del servidor MCP** | Herramientas y detalles de conexión para el servidor MCP |
| **Dirección/hooks** *(opcional)* | Tareas automatizadas que se ejecutan en eventos IDE o mediante comandos de barra diagonal |

---

#### ¿Qué hace que los poderes sean diferentes?

| Característica | Descripción |
|---|---|
| **Carga dinámica de herramientas MCP** | Los servidores MCP tradicionales cargan todas las herramientas por adelantado. Potencia las herramientas de carga bajo demanda, lo que reduce el uso del contexto básico y al mismo tiempo brinda a su agente acceso a docenas de tecnologías |
| **Ecosistema abierto** | Explore poderes seleccionados de socios de lanzamiento, incluidos Datadog, Dynatrace, Figma, Neon, Netlify, Postman, Supabase, Stripe, Strands SDK y AWS Aurora. Instale poderes creados por la comunidad desde las URL de GitHub o cree y comparta los suyos propios |
| **Instalación con un clic** | Explora poderes directamente en Kiro o en kiro.dev. Haga clic en "Instalar" y la energía se registrará automáticamente. Sin archivos de configuración JSON, sin configuración de línea de comandos |

---

### Poderes del socio de lanzamiento

| Socio | Caso de uso |
|---|---|
| **Raya** | Pagos, suscripciones, facturación |
| **Supabase** | Base de datos PostgreSQL, autenticación, almacenamiento |
| **Neón** | PostgreSQL sin servidor |
| **Figura** | Tokens de diseño, especificaciones de componentes |
| **AWS Aurora** | Base de datos relacional administrada |
| **Netlificar** | Implementación de frontend, funciones de borde |
| **Cartero** | Pruebas y documentación de API |
| **Perro de datos** | Monitoreo, registros, APM |
| **Dinatrace** | Plataforma de observabilidad |
| **SDK de hilos** | Desarrollo de agentes |

---

*📂 Capítulo: **Billing***

## Facturación para particulares

> **Fuente:** [kiro.dev/docs/billing/](https://kiro.dev/docs/billing/)

---

Kiro utiliza un sistema de facturación basado en créditos con múltiples niveles diseñados para desarrolladores individuales. Todos los planes incluyen acceso a las funciones principales de IDE; Los niveles difieren según la asignación de crédito y la disponibilidad del modelo.

---

### Niveles de servicio

| Nivel | Créditos Mensuales | Mejor para |
|---|---|---|
| **Gratis** | Limitado | Evaluación y uso de la luz |
| **Pro** | ~1.000 créditos | Desarrolladores individuales activos |
| **Pro+** | Límite superior | Usuarios avanzados con uso intensivo |
| **Poder** | Límite más alto | Usuarios profesionales/de gran volumen |

> Consulte [kiro.dev/pricing](https://kiro.dev/pricing) para conocer los límites de crédito exactos y los precios actuales.

---

### Prácticas de facturación

#### Actualización desde Gratis → Pagado (primera vez)

Si estás en el **nivel Kiro Free**, nunca has actualizado antes y actualiza a Pro, Pro+ o Power a mitad de mes:
- Se te cobra una **tarifa prorrateada** por el resto del mes
- Obtienes acceso inmediato a los **límites de crédito completos** de tu nuevo plan

Si actualiza nuevamente en el mismo mes (por ejemplo, Gratis → Pro el 15 de abril, luego Pro → Pro+ el 20 de abril):
- Las tarifas se **retroceden proporcionalmente** como si hubieras elegido el nivel más alto desde el primer día
- Después de eso, se te cobrará el importe total en el futuro.

#### Actualización entre niveles pagos

Si ya está en un nivel pago y actualiza a un nivel pago superior a mitad de mes:
- Se le cobra una **tarifa retroactiva para todo el mes** según la diferencia de precio
- Kiro recalcula el uso de todo el mes con los créditos del nuevo nivel.

> **Ejemplo:** Usaste 1010 créditos (10 por encima del límite Pro) y luego actualizaste a Pro+. El cargo por excedente se elimina porque su uso cae por debajo del límite Pro+.

> **Nota:** Si estás en un nivel pago, cambia a Gratis y luego vuelve a un nivel pago, el comportamiento de pago es el mismo que si actualizas desde Gratis → Pagado.

#### Degradación

- Las rebajas **entran en vigor el mes siguiente** (las actualizaciones entran en vigor inmediatamente)
- Se le cobrará la **tarifa completa del mes actual** incluso si baja de categoría a mitad de mes

> **Ejemplo:** Si baja de Pro+ a Pro el 2 de junio, se le cobrará la tarifa completa de suscripción Pro+ de junio. A partir de julio se te cobrará la tarifa Pro.

#### Excesos

- Si excede su límite de crédito mensual, se le cobrarán los cargos totales por excedente **al final del ciclo de facturación**

#### Renovación de crédito

- Para **todos los niveles**, su límite de uso se renueva al comienzo del **siguiente ciclo de facturación**

---

### Relacionado

- [Actualizando su plan →](https://kiro.dev/docs/billing/upgrading/)
- [Migración desde VS Code →](https://kiro.dev/docs/guides/migrate-from-vscode/)

---

*📂 Capítulo: **MCP > Configuration***

## Configuración de MCP

> **Fuente:** [kiro.dev/docs/mcp/configuration/](https://kiro.dev/docs/mcp/configuration/)

---

### Estructura del archivo de configuración

Los archivos de configuración MCP usan formato JSON:

```json
{
  "mcpServers": {
    "local-server-name": {
      "command": "command-to-run-server",
      "args": ["arg1", "arg2"],
      "env": {
        "ENV_VAR1": "hard-coded-variable",
        "ENV_VAR2": "${EXPANDED_VARIABLE}"
      },
      "disabled": false,
      "autoApprove": ["tool_name1", "tool_name2"],
      "disabledTools": ["tool_name3"]
    },
    "remote-server-name": {
      "url": "https://endpoint.to.connect.to",
      "headers": {
        "HEADER1": "value1",
        "HEADER2": "value2"
      },
      "disabled": false,
      "autoApprove": ["tool_name1", "tool_name2"],
      "disabledTools": ["tool_name3"]
    }
  }
}
```

#### Propiedades de configuración

**Servidor local:**

| Propiedad | Descripción |
|---|---|
| `comando` | Comando para iniciar el servidor |
| `argumentos` | Argumentos del comando |
| `entorno` | Variables de entorno |
| `deshabilitado` | `true` para deshabilitar sin eliminar |
| `aprobación automática` | Herramientas aprobadas automáticamente |
| `Herramientas deshabilitadas` | Herramientas deshabilitadas individualmente |

**Servidor remoto:**

| Propiedad | Descripción |
|---|---|
| `URL` | Punto final del servidor remoto |
| `encabezados` | Encabezados HTTP (autenticación, etc.) |
| `deshabilitado` | `true` para deshabilitar |
| `aprobación automática` | Herramientas aprobadas automáticamente |
| `Herramientas deshabilitadas` | Herramientas deshabilitadas |

---

### Ubicaciones de configuración

| Nivel | Archivo | Alcance |
|---|---|---|
| **Espacio de trabajo** | `.kiro/settings/mcp.json` | Solo el workspace actual — ideal para servidores específicos del proyecto |
| **Usuario (global)** | `~/.kiro/settings/mcp.json` | Todos los espacios de trabajo — ideales para servidores de uso frecuente |

> Si ambos archivos existen, las configuraciones se **mezclan** y el espacio de trabajo tiene **precedencia**.

---

### Creando archivos de configuración

#### Usando la paleta de comandos
`Cmd+Shift+P` → **"Kiro: Editar configuración de MCP"**

#### Usando el panel Kiro
Kiro Panel → sección MCP → haga clic en el ícono de configuración

---

### Variables de entorno

Muchos servidores MCP requieren variables de entorno para autenticación:

```json
{
  "mcpServers": {
    "server-name": {
      "env": {
        "API_KEY": "${YOUR_API_KEY}",
        "DEBUG": "true",
        "TIMEOUT": "30000"
      }
    }
  }
}
```

> ⚠️ Por seguridad, Kiro solo expande variables de entorno **explícitamente aprobadas**. Kiro muestra una ventana emergente de advertencia al detectar variables no aprobadas. Para gestionarlas: Configuración → buscar **"Mcp Approved Env Vars"**.

---

### Deshabilitar servidores temporalmente

Para deshabilitar un servidor sin eliminar su configuración:

```json
{
  "mcpServers": {
    "server-name": {
      "disabled": true
    }
  }
}
```

---

### Consideraciones de seguridad

- Usá referencias a variables de entorno ("${API_TOKEN}`) en lugar de codificar valores sensibles
- Nunca comete archivos de configuración con credenciales a control de versiones
- Conectar solo a servidores remotos de confianza
- Revisará los permisos de las herramientas antes de agregarlos a `autoApprove`

---

### Solución de problemas de configuración

| Problema | Solución |
|---|---|
| JSON inválido | Verificá sintaxis — comas, comillas, corchetes |
| Comando no encontrado | Verifica que el comando existe en tu `PATH` |
| Variables no expandidas | Verificar que la variable está en la lista de aprobadas |
| Cambios no aplicados | Guardá el archivo (`Cmd+S`) — los servidores se reconectan automáticamente |

---

*📂 Capítulo: **MCP > Server directory***

## Directorio del servidor MCP

> **Fuente:** [kiro.dev/docs/mcp/servers/](https://kiro.dev/docs/mcp/servers/)

---

### Servidores disponibles

Kiro incluye un directorio curador de servidores MCP con instalación con un clic. Podés explorarlos directamente en el panel de Kiro o en [kiro.dev/docs/mcp/servers/](https://kiro.dev/docs/mcp/servers/).

#### Servidores destacados

| Servidor | Comando de instalacion | Requerir |
|---|---|---|
| **Documentos de AWS** | `uvx awslabs.aws-documentation-mcp-server@latest` | UV |
| **GitHub** | URL: `https://api.githubcopilot.com/mcp/` | Ficha |
| **Contexto7** | `npx -y @upstash/context7-mcp` | Nodo |
| **Git** | `uvx mcp-servidor-git` | UV |
| **Acoplador** | `npx -y @modelcontextprotocol/server-docker` | Nodo |
| **Sistema de archivos** | `npx -y @modelcontextprotocol/server-filesystem` | Nodo |
| **Azul** | `npx -y @modelcontextprotocol/server-azure` | Nodo + suscripción |
| **GCloud** | `npx -y @google-cloud/gcloud-mcp` | Nodo |
| **Perro de datos** | URL: `https://mcp.datadoghq.com/...` | Clave API |
| **Amplitud** | URL: `https://mcp.amplitude.com/mcp` | — |
| **Herramientas de desarrollo de Chrome** | `npx -y chrome-devtools-mcp@latest` | Nodo |
| **Dinatrace** | `npx -y @dynatrace-oss/dynatrace-mcp-server@latest` | Nodo + URL |

---

### Comparte tu servidor MCP

#### Instalar esquema de enlace

Podés crear enlaces de instalación para que otros instalen tu servidor con un clic:

```
https://kiro.dev/launch/mcp/add?name=<server-name>&config=<url-encoded-config>
```

#### Generar un enlace de instalación

**JavaScript/Mecanografiado:**
```javascript
función createKiroInstallLink(nombre, configuración) {
  const nombrecodificado = encodeURIComponent(nombre);
  const encodedConfig = encodeURIComponent(JSON.stringify(config));
  devolver `https://kiro.dev/launch/mcp/add?name=${encodedName}&config=${encodedConfig}`;
}

// Ejemplo: servidor local
enlace constante = createKiroInstallLink('aws-docs', {
  comando: 'uvx',
  argumentos: ['awslabs.aws-documentation-mcp-server@latest'],
  entorno: { FASTMCP_LOG_LEVEL: 'ERROR' },
  deshabilitado: falso,
  aprobación automática: []
});
```

**Python:**
```pitón
importar json
de urllib.parse cotización de importación

def create_kiro_install_link(nombre: str, configuración: dict) -> str:
    nombre_codificado = cita(nombre)
    codificado_config = cita (json.dumps (config))
    devolver f"https://kiro.dev/launch/mcp/add?name={encoded_name}&config={encoded_config}"
```

---

### Descubra más servidores MCP

#### Recursos oficiales
- [Registro MCP](https://github.com/modelcontextprotocol/registry) — Registro oficial con servidores contribuyentes por la comunidad
- [Model Context Protocol Org](https://github.com/modelcontextprotocol) — Implementaciones de referencia del equipo MCP

#### Registros de paquetes
- [npm](https://www.npmjs.com/search?q=mcp-server) — Buscar `mcp-server` o `@modelcontextprotocol/server-*`
- [PyPI](https://pypi.org/search/?q=mcp-server) — Buscar `mcp-server` para implementaciones Python

---

*📂 Capítulo: **MCP > Tools***

## Herramientas MCP

> **Fuente:** [kiro.dev/docs/mcp/usage/](https://kiro.dev/docs/mcp/usage/)

---

Una vez configurados los servidores MCP, podrás usar sus herramientas directamente desde el chat.

---

### Interactuar con herramientas MCP

#### Preguntas directas

La forma más simple — hacé preguntas relacionadas al dominio del servidor:

```
Tell me about Amazon Bedrock
How do I configure S3 bucket policies?
```

Kiro selecciona automáticamente la herramienta MCP apropiada basada en tu pregunta.

#### Solicitudes de herramientas específicas

Describí lo que querés hacer:

```
Search AWS documentation for information about ECS task definitions
Get recommendations for AWS CloudFormation best practices
```

#### Contexto explícito

Para mayor control, especifique el servidor y la herramienta directamente:

```
##[aws-docs] search_documentation Tell me about AWS Lambda
```

Formato: `#[nombre-servidor] mensaje nombre_herramienta`

---

### Panel de herramientas MCP

Accedé al panel de MCP Tools para gestionar las herramientas disponibles:

#### Gestión de herramientas individuales

- Ver todas las herramientas disponibles por servidor.
- Habilitar o deshabilitar herramientas individuales
- Ver parámetros y descripción de cada herramienta.

#### Acciones a nivel de servidor

- Reiniciar un servidor MCP
- Ver registros del servidor
- Editar la configuración del servidor

---

### Proceso de aprobación de herramientas

Cuando Kiro quiera usar una herramienta MCP, solicita aprobación primero:

1. Aparece un mensaje que describe la herramienta y su propósito.
2. Revisarás los detalles de la herramienta y los parámetros.
3. Haga clic en **Aprobar** para permitir, o **Denegar** para bloquear.

#### Herramientas confiables de aprobación automática

Para herramientas de confianza de uso frecuente, configure `autoApprove` en `mcp.json`:

```json
{
  "mcpServers": {
    "aws-docs": {
      "autoApprove": [
        "mcp_aws_docs_search_documentation",
        "mcp_aws_docs_read_documentation"
      ]
    }
  }
}
```

---

### Ejemplos por tipo de servidor

#### Servidor de documentación de AWS

```
##Buscar documentación
Busque en la documentación de AWS el control de versiones del depósito S3

## Leer documentación específica
Lea la documentación de las URL de la función AWS Lambda

##recomendaciones Obtener
Encuentre contenido relacionado con las definiciones de tareas de AWS ECS
```

#### Servidor MCP de GitHub

```
## Información del repositorio
Muéstrame información sobre el repositorio tensorflow/tensorflow

## Búsqueda de código
Encuentre ejemplos de hooks de React en facebook/react

## Gestión de emisiones
Crear un problema en mi repositorio sobre el error de inicio de sesión
```

---

### Técnicas de uso avanzadas

#### Encadenamiento de herramientas MCP

Combina múltiples herramientas en una sola conversación para tareas complejas. Por ejemplo, busque documentación AWS y luego cree un problema en GitHub con el resultado.

#### Combinando con el contexto local

Combina herramientas MCP con contexto local agregando archivos al contexto para que el agente pueda relacionar documentación externa con tu código actual.

#### Uso de herramientas MCP en especificaciones

Las herramientas MCP están disponibles durante la creación de Specs. Podés referenciarlos en el plan de implementación para que el agente los use durante la ejecución.

---

### Avisos de MCP

Algunos servidores MCP exponen **indicaciones predefinidas** — plantillas de indicaciones con parámetros:

#### Acceso a indicaciones
Escribí `/` en el chat → los avisos MCP disponibles aparecerán junto a hooks y archivos de Steering.

#### Indicaciones con argumentos
Los avisos pueden aceptar argumentos. Kiro te preguntará los valores necesarios antes de ejecutar el aviso.

---

### Plantillas de recursos de MCP

Algunos servidores proporcionan **plantillas de recursos** — patrones de URI para acceder a recursos dinámicos:

#### Acceso a plantillas de recursos
Las plantillas aparecen en el panel de MCP Tools bajo cada servidor.

#### Completar los parámetros de la plantilla
Completará los parámetros de la plantilla (ej. ID de repositorio, nombre de depósito) y Kiro generará el URI correcto para acceder al recurso.

---

### Mejores prácticas

- Sé específico en tus solicitudes para obtener los resultados más relevantes.
- Empezá con preguntas directas antes de usar referencias específicas de herramientas.
- Auto-aprobá solo herramientas de confianza que usas frecuentemente
- Combiná herramientas MCP con contexto local para mejores resultados
- Revisá los parámetros de la herramienta antes de aprobar para asegurarte que son correctos.

---

*📂 Capítulo: **MCP > Best practices***

## Mejores prácticas de MCP

> **Fuente:** [kiro.dev/docs/mcp/security/](https://kiro.dev/docs/mcp/security/)

---

### Configuración segura

#### Protección de claves y tokens API

1. **Nunca comités** archivos de configuración con tokens sensibles a control de versiones
2. Crear tokens con **permisos mínimos** necesarios para el servidor MCP (ej. usa tokens de acceso personal de grano fino para GitHub en lugar de tokens clásicos)
3. Limitá el alcance de acceso solo a los repositorios o recursos necesarios
4. **Rotá regularmente** las claves API y tokens usados en la configuración
5. Usá **variables de entorno** siempre que sea posible en lugar de codificar valores

#### Ejemplo: uso de variables de entorno

En lugar de codificar tokens:

```json
{
  "mcpServers": {
    "github": {
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_TOKEN}"
      }
    }
  }
}
```

Configura la variable de entorno en tu shell:

```bash
export GITHUB_TOKEN=your-token-value
```

#### Variables de entorno aprobadas

Por seguridad, Kiro solo expande variables de entorno **explícitamente aprobadas**. Cuando agrega o modifica una configuración MCP con variables no aprobadas, Kiro muestra una ventana emergente de advertencia.

Para gestionar las variables aprobadas:
1. Configuración de Abrí Kiro
2. Buscá **"Mcp Approved Env Vars"**
3. Agrega las variables que quieras permitir

#### Permisos del archivo de configuración

Restringí el acceso a tus archivos de configuración MCP:

```golpecito
## Configuración a nivel de usuario
chmod 600 ~/.kiro/settings/mcp.json

## Configuración a nivel del espacio de trabajo
chmod 600 .kiro/settings/mcp.json
```

---

### Uso seguro de herramientas

#### Proceso de aprobación de herramientas

1. Revisá cada solicitud de herramienta cuidadosamente antes de aprobar
2. Verificá los parámetros que se pasan al herramienta
3. Entendé qué va a hacer la herramienta antes de aprobar
4. Denegá cualquier solicitud sospechosa que no coincida con tu tarea actual

#### Pautas de aprobación automática

Solo aprobará automáticamente las herramientas que:
1. No tienen acceso de escritura a sistemas sensibles
2. Provienen de fuentes de confianza con código verificado
3. Son de uso frecuente en tu flujo de trabajo
4. Tienen alcance limitado de acceso

```json
{
  "mcpServers": {
    "aws-docs": {
      "autoApprove": [
        "mcp_aws_docs_search_documentation",
        "mcp_aws_docs_read_documentation"
      ]
    }
  }
}
```

---

### Aislamiento del espacio de trabajo

#### Uso de configuraciones a nivel de espacio de trabajo

Para proyectos con diferentes requisitos de seguridad, use configuraciones a nivel de espacio de trabajo (`.kiro/settings/mcp.json`) en lugar de la configuración global del usuario:

- Limitá los servidores MCP disponibles por proyecto
- Configurará permisos específicos para el espacio de trabajo
- Evitará exponer servidores de producción en proyectos de desarrollo.

---

### Monitoreo y Auditoría

#### Comprobación de registros de MCP

Revise periódicamente los registros MCP para monitorear la actividad del servidor:

1. Abrí el panel de Kiro
2. Seleccione la pestaña **Salida**
3. Elegí **"Kiro - MCP Logs"** del menú desplegable

#### Uso de la herramienta de auditoría

Periódicamente revisá qué herramientas ha aprobado:

1. Verifica tu configuración MCP para herramientas aprobadas automáticamente
2. Revisá los logs MCP para patrones de uso
3. Monitoreá la actividad del servidor en busca de comportamiento inesperado
4. Elimina la aprobación automática de herramientas que ya no usás frecuentemente

---

### Respondiendo a incidentes de seguridad

Si sospecha que un servidor MCP fue confirmado o está actuando de forma inesperada:

1. **Deshabilitar el servidor** inmediatamente: `"disabled": true` en la configuración
2. **Revocar tokens** comprometidos desde la plataforma correspondiente (GitHub, AWS, etc.)
3. **Revisar logs** para entender el alcance del problema
4. **Rotar credenciales** antes de rehabilitar el servidor

---

### Medidas de seguridad adicionales

#### Seguridad de la red

- Conectar solo a servidores remotos con HTTPS
- Verifica certificados SSL de terminales remotos
- Considerá usar un proxy corporativo para servidores remotos en entornos empresariales

#### Seguridad del sistema

- Mantené actualizado los paquetes npm/uvx de los servidores MCP
- Revise los registros de cambios de servidores MCP antes de actualizar
- Ejecutá servidores MCP con permisos mínimos del sistema operativo

---

*📂 Capítulo: **Guides > Language support***

## Soporte de idiomas

> **Fuente:** [kiro.dev/docs/guides/languages-and-frameworks/](https://kiro.dev/docs/guides/languages-and-frameworks/)

---

Kiro proporciona capacidades de desarrollo asistido por IA para los lenguajes más populares, ayudándote a escribir, debuguear y mantener código de forma más eficiente.

---

### Mecanografiado y JavaScript

> [kiro.dev/docs/guides/languages-and-frameworks/typescript-javascript-guide/](https://kiro.dev/docs/guides/languages-and-frameworks/typescript-javascript-guide/)

#### Requisitos previos
- [Node.js](https://nodejs.org/) — última versión
- [TypeScript](https://www.typescriptlang.org/) — global o local en el proyecto
- Gestor de paquetes: npm, Yarn o pnpm
-[Git](https://git-scm.com/)

#### Extensiones sugeridas

| Extensión | Propósito |
|---|---|
| [ESLint](https://open-vsx.org/extension/dbaeumer/vscode-eslint) | Linting en tiempo real |
| [Más bonita](https://open-vsx.org/extension/esbenp/prettier-vscode) | Formato automático |
| [Etiqueta de cambio de nombre automático](https://open-vsx.org/extension/formulahendry/auto-rename-tag) | Renombrado automático de etiquetas HTML/JSX |
| [Fragmentos de ES6](https://open-vsx.org/extension/xabikos/JavaScriptSnippets) | Fragmentos de JavaScript/TypeScript modernos |

#### Steering

Kiro puede generar archivos de Steering para tus proyectos TS/JS:

- `product.md` — Información del producto y sus características clave
- `tech.md` — Stack tecnológico y pautas de desarrollo
- `structure.md` — Organización del proyecto

#### Hooks recomendados

| Gancho | Gatillo | Acción |
|---|---|---|
| **Generación de prueba** | Guardar archivo (`.ts/.tsx`) | `"Crear un gancho que genere pruebas Jest cuando guardo un nuevo componente"` |
| **Comprobación de tipo** | Guardar archivo | `"Configurar un enlace para ejecutar la verificación de tipos de TypeScript cuando guardo archivos"` |
| **Actualización de dependencia** | Guardar archivo (`paquete.json`) | `"Crear un gancho que busque paquetes npm obsoletos"` |
| **Corrección automática de ESLint** | Guardar archivo | Corre ESLint con `--fix` y reporta los problemas restantes |
| **Documentos de los componentes** | Guardar archivo (`.tsx`) | Accesorios adicionales, genera JSDoc y actualiza el README |

---

### Pitón

> [kiro.dev/docs/guides/languages-and-frameworks/python-guide/](https://kiro.dev/docs/guides/languages-and-frameworks/python-guide/)

#### Requisitos previos
- Python 3.8+ ([descargar](https://www.python.org/downloads/))
- pip (incluido con Python)
- Entorno virtual: `venv`, `virtualenv` o `conda`
-Git

#### Extensiones sugeridas

| Extensión | Propósito |
|---|---|
| [Python](https://open-vsx.org/extension/ms-python/python) | IntelliSense, depuración, linting, formateo |
| [PyLint](https://open-vsx.org/extension/ms-python/pylint) | Linting para archivos Python |
| [Jupyter](https://open-vsx.org/extension/ms-toolsai/jupyter) | Soporte para portátiles |
| [Depurador de Python](https://open-vsx.org/extension/ms-python/debugpy) | Depuración con debugpy |
| [Arcoíris CSV](https://open-vsx.org/extension/mechatroner/rainbow-csv) | Visualización de CSV/TSV |

#### Ejemplo de dirección: `python-conventions.md`

```markdown
## Convenciones de Python

### Convenciones de nomenclatura
- Snake_case para variables y funciones.
- PascalCase para clases
- UPPER_SNAKE_CASE para constantes

### Estilo de código
- Seguir PEP 8
- Usar Black para formatear
- Máximo 88 caracteres por línea
- Escribe sugerencias en todas las funciones públicas.

### Documentación
- Docstrings para todas las funciones y clases públicas
- Estilo Google o NumPy
```

#### Hooks recomendados

| Gancho | Gatillo | Aviso |
|---|---|---|
| **Generación de prueba** | Guardar archivo (`.py`) | `"Crear un gancho que genere pruebas de pytest cuando guardo un nuevo módulo de Python"` |
| **Actualización de dependencia** | Guardar archivo (`requisitos.txt`) | `"Crear un gancho que busque paquetes de pip obsoletos"` |
| **pelusa** | Guardar archivo (`.py`) | Corre flake8/pylint, informa problemas, sugiere correcciones, actualiza cadenas de documentos |
| **Entorno virtual** | Guardar archivo (`requirements.txt` / `pyproject.toml`) | Verifica venv, instala deps, reporta conflictos |

---

###Java

> [kiro.dev/docs/guides/languages-and-frameworks/java-guide/](https://kiro.dev/docs/guides/languages-and-frameworks/java-guide/)

#### Requisitos previos
- JDK 17+ (se recomienda [Amazon Corretto](https://aws.amazon.com/corretto/))
- Herramienta de construcción: Maven o Gradle
-Git

#### Extensiones sugeridas

| Extensión | Propósito |
|---|---|
| [Paquete de extensión para Java](https://open-vsx.org/extension/vscjava/vscode-java-pack) | IntelliSense, Depuración, Pruebas, Maven, Gerente de Proyecto |
| [Paquete de extensión Spring Boot](https://open-vsx.org/extension/vmware/vscode-spring-boot) | Herramientas de arranque de primavera + Inicializr + Panel de control |
| [Gradle para Java](https://open-vsx.org/extension/vscjava/vscode-gradle) | Gestión de proyectos Gradle |
| [Maven para Java](https://open-vsx.org/extension/vscjava/vscode-maven) | Gestión de proyectos Maven |

#### Ejemplos de dirección

**`java-conventions.md`** — Patrones arquitectónicos y pruebas:
```markdown
## Convenciones del proyecto Java
### Patrones de arquitectura
- Arquitectura hexagonal para dominios complejos
- CQRS para separación lectura/escritura
### Estrategia de prueba
- Pruebas unitarias para toda la lógica de negocio.
- TestContainers para pruebas de integración
- 80% de cobertura de código mínimo
- Patrón AAA (Ordenar, Actuar, Afirmar)
```

**`spring-boot-patterns.md`** — Directrices para Spring Boot:
```markdown
## Pautas de desarrollo de Spring Boot
### Estructura de componentes
- @RestController para puntos finales REST
- @Service para lógica de negocio
- @Repository para acceder a datos
### Inyección de dependencia
- Inyección de constructor (sin inyección de campo)
- Usar campos finales para dependencias inyectadas
```

---

*📂 Capítulo: **Guides > Learn by playing***

## Aprende jugando

> **Fuente:** [kiro.dev/docs/guides/learn-by-playing/](https://kiro.dev/docs/guides/learn-by-playing/)

---

Kiro ofrece un recorrido interactivo de aprendizaje donde podrás aprender AI Engineering completando tareas reales dentro de un videojuego. No solo podés personalizar el juego — también podés personalizar Kiro extendiendo su contexto y comportamientos con Model Context Protocol (MCP).

---

### Ruta de aprendizaje

El tutorial está estructurado en etapas progresivas:

| Etapa | Contenido |
|---|---|
| **00 - Configuración** | Configurar el entorno de desarrollo y lanzar el juego |
| **01–06 - Tareas** | Completar tareas dentro del juego usando las capacidades de Kiro |
| **07 - Ampliando Kiro con MCP** | Extensor Kiro con servidores MCP para capacidades adicionales |
| **99 - Conclusión** | Cierre del recorrido y próximos pasos |

---

### Empezando

1. Ir a [kiro.dev/docs/guides/learn-by-playing/00-setup/](https://kiro.dev/docs/guides/learn-by-playing/00-setup/)
2. Siga las instrucciones para configurar el entorno de desarrollo.
3. Lanzar el juego y comenzar las tareas guiadas
4. A medida que completes las tareas, aprende las funcionalidades clave de Kiro

---

### Lo que aprenderás

- Capacidades del chat y modos de trabajo (Vibe vs Spec)
- Creación y gestión de Hooks para automatizar el flujo de trabajo.
- Configuración de servidores MCP para ampliar las capacidades
- Uso de Steering para guiar el comportamiento del agente
- Integración de Kiro en un flujo de desarrollo real

---

### Relacionado

- [Configuración MCP →](../10_MCP/01_Configuration.md)
- [Hooks →](../07_Hooks/01_Hook%20triggers.md)
- [Poderes →](../06_Powers/01_Install%20powers.md)

---

*📂 Capítulo: **Guides > Migrating from VSCode***

## Migrar desde VS Code

> **Fuente:** [kiro.dev/docs/guides/migrating-from-vscode/](https://kiro.dev/docs/guides/migrating-from-vscode/)

---

La base de VS Code de Kiro permite compatibilidad completa con tu entorno de desarrollo. Podés transferir tu configuración personalizada (extensiones, temas, configuraciones y accesos directos) sin problemas de compatibilidad.

---

### Migración de perfil

#### Exportación de un perfil desde VS Code

1. Abra la paleta de comandos en VS Code (`Cmd/Ctrl + Shift + P`)
2. Escribí y seleccioná **"Preferencias: Abrir perfiles (UI)"**
3. Localice el perfil deseado en la barra lateral
4. Accedé al menú de 3 puntos y elige **Exportar**
5. Guarda localmente o publica en un GitHub Gist

#### Importando un perfil a Kiro

1. Abra la paleta de comandos de Kiro (`Cmd/Ctrl + Shift + P`)
2. Escribí y seleccioná **"Preferencias: Abrir perfiles (UI)"**
3. Abra el menú desplegable junto a **Nuevo perfil** y seleccione **Importar perfil**
4. Pega la URL del GitHub Gist o busca tu archivo de exportación local
5. Confirma con **Importar** para guardar la configuración
6. Activa tu perfil seleccionándolo en la barra lateral y haciendo clic en la marca de verificación ✓

**Tu perfil importado incluye:**
- Temas de color y preferencias de UI
- Configuraciones del editor y espacio de trabajo
- Atajos de teclado y combinaciones de teclas personalizados

---

### Configuración e interfaz

#### Menús de configuración

Kiro amplía la arquitectura de configuración de VS Code con controles dedicados para capacidades de IA:

**Configuración de Kiro:**
- `Cmd/Ctrl + Shift + P` → "Preferencias: Abrir Configuración (UI)"
- Navegá a la sección **Kiro Agent**
- Gestioná comportamientos de IA, automatización del agente, comandos confiables y características exclusivas de Kiro

**Configuración del código VS:**
- Mismo acceso: `Cmd/Ctrl + Shift + P` → "Preferencias: Abrir Configuración (UI)"
- Tus preferencias estándar de VS Code siguen funcionando junto a las configuraciones de Kiro

#### Actualizaciones de versión

Kiro se mantiene sincronizado con el ciclo de desarrollo de VS Code mediante rebase regular. Se incorporan las últimas características seleccionando versiones estables de VS Code para asegurar confiabilidad junto a las mejoras de IA.

---

### Compatibilidad de extensiones

Kiro usa el **registro de extensiones OpenVSX**, asegurando compatibilidad con extensiones de código abierto.

| Tipo de extensión | Compatibilidad |
|---|---|
| **Extensiones de idiomas** | Funcionalidad completa para extensiones disponibles en OpenVSX |
| **Extensiones de tema** | Compatibilidad visual completa con temas de OpenVSX |
| **Extensiones de depuración** | Flujos de trabajo de depuración sin interrupciones para extensiones compatibles |
| **Extensiones de Git** | Aumentadas con generación inteligente de commits y revisión de código automatizada |

> ⚠️ Solo las extensiones disponibles en el **registro OpenVSX** pueden importarse. Algunas extensiones exclusivas del VS Code Marketplace pueden no estar disponibles en Kiro.

---

### Lista de verificación rápida

- [] Exportar perfil de VS Code (extensiones, configuraciones, combinaciones de teclas)
- [] Importar perfil en Kiro
- [] Verificar que las extensiones críticas estén disponibles en OpenVSX
- [] Revisar los ajustes de **Kiro Agent** para configurar el comportamiento de IA
- [ ] Probar el flujo de trabajo habitual para confirmar compatibilidad

---

*📂 Capítulo: **Privacy and security***

## Privacidad y seguridad

> **Fuente:** [kiro.dev/docs/privacy-and-security/](https://kiro.dev/docs/privacy-and-security/)

---

Kiro proporciona varias funciones de seguridad para ayudarle a mantener el control sobre su entorno de desarrollo. Comprender estas características le ayudará a implementar medidas de seguridad adecuadas para sus necesidades específicas.

---

### Obtención de URL

En el módulo de chat de Kiro, puede pegar una URL específica para que su dispositivo la recupere y la use como contexto. Usted es responsable del contenido de la URL que obtiene y de asegurarse de que su uso cumpla con los términos y leyes de terceros aplicables.

---

### Piloto automático versus modo supervisado

Kiro opera en dos modos. **El piloto automático está habilitado de forma predeterminada.**

#### Modo piloto automático

En modo Piloto automático, Kiro funciona **de forma autónoma**:
- Ejecuta múltiples pasos sin requerir aprobación para cada uno
- Toma decisiones basadas en su comprensión de sus requisitos.
- Incluye creación, modificación, búsqueda y eliminación de archivos.
- Puede ejecutar comandos que impactan el sistema de archivos
- Puedes activar o desactivar el piloto automático en la interfaz de chat en cualquier momento
- Puedes **interrumpir el piloto automático en cualquier momento** para recuperar el control manual

#### Modo supervisado

En modo supervisado, Kiro trabaja **interactivamente** con el usuario:
- Sugiere acciones (creación, modificación, eliminación de archivos) pero **espera la commit del usuario** antes de continuar
- Hace preguntas aclaratorias cuando es necesario.
- Puedes revisar y aprobar cada documento generado o cambio de código.
- Mantiene el control total sobre el proceso de desarrollo.

#### Ver y revertir cambios

En cualquier modo, puedes:
- Ver cambios individuales o de todos los archivos seleccionando **"Ver todos los cambios"** en el módulo de Chat
- Seleccione **"Revertir todos los cambios"** para deshacer todas las modificaciones del agente
- Revertir a un [punto de control](https://kiro.dev/docs/chat/checkpoints) para restaurar archivos a un estado anterior localmente

---

### Comandos confiables

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

### Mejores prácticas

Las siguientes son pautas generales; no representan una solución de seguridad completa. Evalúe lo que es apropiado para su entorno.

#### Protegiendo sus recursos

Al utilizar GitHub o la autenticación de Google con Kiro, tenga en cuenta que el agente de Kiro opera dentro de su entorno local y puede acceder a:
- Archivos y repositorios locales
- Variables de entorno
- Credenciales de AWS almacenadas en su entorno
- Otros archivos de configuración con información sensible

#### Recomendaciones

**1. Aislamiento del espacio de trabajo**
- Mantenga los proyectos confidenciales en espacios de trabajo separados
- Utilice `.gitignore` (o `.kiroignore`) para evitar el acceso a archivos confidenciales
- Considere utilizar funciones de confianza del espacio de trabajo en su IDE

**2. Utilice un entorno limpio**
- Considere la posibilidad de crear una cuenta de usuario dedicada o un entorno de contenedor para Kiro.
- Limite el acceso solo a los repositorios y recursos necesarios para su proyecto actual

**3. Administre las credenciales de AWS con cuidado**
- Utilice credenciales temporales con los permisos adecuados
- Considere el uso de perfiles con nombre de AWS para aislar el acceso de Kiro
- Para trabajos confidenciales, elimine las credenciales de AWS de su entorno cuando no las necesite

**4. Control de acceso al repositorio**
- Al usar la autenticación de GitHub, revise a qué repositorios puede acceder Kiro
- Utilice tokens de acceso específicos del repositorio cuando sea posible
- Auditar periódicamente los permisos de acceso.

---

### Seguridad de extensiones remotas

El soporte de extensiones remotas sigue el mismo modelo de seguridad que las extensiones locales. Cuando se utiliza desarrollo remoto (SSH, contenedores, WSL), las extensiones se ejecutan en el entorno remoto con los permisos del usuario remoto. Asegúrese de que los entornos remotos estén correctamente protegidos y que solo se instalen extensiones confiables.

---

*📂 Capítulo: **Billing for individuals > Upgrading your plan***

## Actualizando su plan

> **Fuente:** [kiro.dev/docs/billing/upgrading/](https://kiro.dev/docs/billing/upgrading/)

---

### Actualización por primera vez (Gratis → Pagado)

Si nunca antes has comprado un plan, sigue estos pasos:

1. En Kiro, selecciona el ícono de perfil
2. Elegí **Plan de actualización**
3. Selecciona el plan al que quieres actualizar
4. Presioná **Open** — serás redirigido al navegador para completar el proceso
5. Confirmá los detalles del plan e ingresa tu correo electrónico
6. Seleccioná tu método de pago, ingresa los detalles y elige **Suscríbete**
7. Después de confirmar, seleccione **Comenzar** para volver al IDE

> ⚠️ Actualmente solo puedes actualizar un AWS Builder ID si **no está vinculado** a una cuenta AWS. Los pagos son procesados ​​por Stripe / Amazon Web Services, Inc.

---

### Actualización de un plan pago existente

Una vez que ya hiciste la primera actualización, el flujo es diferente desde Kiro:

1. En Kiro, selecciona el ícono de perfil
2. Elegí **Manage Plan** — serás redirigido al navegador
3. Elegí **Actualizar suscripción**, seleccioná el plan deseado y luego **Continuar**
4. Confirmá los detalles y elegí **Confirmar**
5. Seleccione **Return to Kiro** para volver al IDE

---

### Resumen de prácticas de facturación

| Situación | Comportamiento |
|---|---|
| Gratis → Pagado (primer mes) | Carga prorrateada por los días restantes; acceso inmediato a los créditos completos del plan |
| Pagado → Mejor pagado (mismo mes) | Cargo retroactivo por la diferencia; el uso del mes se recalcula bajo los límites del nuevo plan |
| Bajar de categoría | Efectivo el próximo mes; se cobra el plan actual por el mes completo |
| Excedentes | Se cobrarán al final del ciclo de facturación |
| Restablecer créditos | Al inicio de cada ciclo de facturación |

---

*📂 Capítulo: **Billing for individuals > Downgrading your plan***

## Degradar su plan

> **Fuente:** [kiro.dev/docs/billing/downgrading/](https://kiro.dev/docs/billing/downgrading/)

---

Se te factura al primer día del mes. Si bajas de plan a mitad del mes, permanecés en el plan actual hasta el final del mes. El nuevo plan comienza el próximo ciclo de facturación y se cobrarán los excedentes del mes actual.

### Pasos

1. En Kiro, selecciona el ícono de perfil
2. Elegí **Manage Plan** — serás redirigido al navegador para completar el proceso
3. En el navegador, elija **Actualizar suscripción**, seleccione el plan al que querrás bajar y luego **Continuar**
4. Confirmá los detalles del plan y elegí **Confirmar**
5. Seleccione **Return to Kiro** para volver al IDE

> ℹ️ Los downgrades **toman efecto el mes siguiente**. Las actualizaciones son efectivos de forma **inmediata**.

---

*📂 Capítulo: **Billing for individuals > Cancelling your plan***

## Cancelar tu plan

> **Fuente:** [kiro.dev/docs/billing/cancelling/](https://kiro.dev/docs/billing/cancelling/)

---

Se te factura al primer día del mes. Si cancelás a mitad del mes, permanecerás en el plan actual hasta fin de mes. Desde el próximo ciclo pasó a **Kiro Free** sin carga mensual. Sin embargo, serás responsable por los excedentes del último mes de pago.

### Pasos

Para cancelar un plan de pago, debes cambiar el nivel **Kiro Free**:

1. En Kiro, selecciona el ícono de perfil
2. Elegí **Manage Plan** — serás redirigido al navegador
3. Elegí **Actualizar suscripción**, seleccioná **Kiro Free** y luego **Continuar**
4. Confirmá los detalles y elegí **Confirmar**
5. Seleccione **Return to Kiro** para volver al IDE

> ⚠️ En el nivel Kiro Free, no hay excedentes disponibles. Al alcanzar el límite mensual debes esperar al próximo mes o actualizar.

---

*📂 Capítulo: **Billing for individuals > Enabling overages***

## Habilitación de excedentes

> **Fuente:** [kiro.dev/docs/billing/overages/](https://kiro.dev/docs/billing/overages/)

---

Los excedentes son cargos adicionales que AWS cobra cuando superas los límites de crédito predefinidos en tu plan. Están **deshabilitados por defecto**.

> ❌ No podrás acumular excedentes en el nivel **Kiro Free**. Al alcanzar el límite deberás esperar al siguiente mes.

---

### ¿Por qué permitir excedentes?

| Ventaja | Descripción |
|---|---|
| **Productividad ininterrumpida** | Continuás trabajando sin fricción al superar la cuota |
| **Mejor información de uso** | Obtenés datos más precisos sobre tu consumo real para elegir el plan correcto |

---

### Habilitación de excedentes

1. En Kiro, selecciona el ícono de perfil
2. En la sección **Excedentes**, active el interruptor asociado

---

*📂 Capítulo: **Billing for individuals > Managing your payments***

## Administrar sus pagos

> **Fuente:** [kiro.dev/docs/billing/managing/](https://kiro.dev/docs/billing/managing/)

---

### Acceso a la información de facturación

1. En Kiro, selecciona el ícono de perfil
2. Elegí **Manage Plan** — serás redirigido al navegador

En el tablero de facturación encontrarás:

| Sección | Información |
|---|---|
| **Suscripción actual** | Plan activo, próxima fecha y monto de facturación, estado |
| **Método de pago** | Métodos de pago guardados, agregar/actualizar tarjetas |
| **Información de facturación** | Dirección de facturación, NIF (si aplica) |
| **Historial de facturas** | Facturas pasadas, descargar PDF, fechas y montos |

---

### Actualizando su método de pago

![Actualizar pago](https://kiro.dev/videos/update-paid.mp4)

1. En Kiro, selecciona el ícono de perfil
2. Elegí **Administrar Plan**
3. Elija **Agregar método de pago** o edite el existente
4. Ingresá los datos de la nueva tarjeta y tu dirección de facturación
5. Si aplica, complete la autenticación 3D-Secure
6. Elija **Agregar** para guardar el método de pago

> Aceptamos todas las tarjetas de crédito y débito principales. La carga se realiza en **USD**.

---

### Ver el historial de facturación y descargar facturas

1. En Kiro, selecciona el ícono de perfil
2. Elegí **Administrar Plan**
3. En la sección **Historial de facturas**, seleccione cualquier factura para ver sus detalles y descargarla como PDF

---

### Solución de problemas de pago

Cuando un pago falla:
- Recibirás una notificación por correo electrónico
- El estado de la suscripción cambiará a **"vencido"**
- Perderás acceso a las características pagas

El sistema reintenta los pagos fallidos automáticamente durante varios días. Una vez que el pago sea exitoso, el acceso se restaura de inmediato.

| Causa común | Solución |
|---|---|
| Tarjeta vencida | Actualizá el método de pago |
| Fondos insuficientes | Verifique el saldo disponible |
| Banco bloqueó la carga | Contacta con tu banco |

---

*📂 Capítulo: **Billing for individuals > Managing usage notifications***

## Administrar notificaciones de uso

> **Fuente:** [kiro.dev/docs/billing/proactive-usage-notifications/](https://kiro.dev/docs/billing/proactive-usage-notifications/)

---

Kiro envía notificaciones proactivas para mantenerte informado sobre tu consumo de créditos.

---

### Tipos de notificación

#### Notificaciones de recursos bajos

Al alcanzar el **80% del uso mensual de créditos**, Kiro envía una notificación:

| Situación | Notificación |
|---|---|
| **Nivel gratuito** | Sugerencia para actualizar; recordatorio de que los créditos se restablecen mensualmente y no hay excedentes |
| **Pagado (puede actualizar)** | Opción de actualizar para más créditos o habilitar excedentes |
| **Pagado (nivel máximo)** | Opción de habilitar excedentes para acceso ininterrumpido |

#### Notificaciones excedentes

Al superar el límite mensual con excedentes habilitados:
- Si puede actualizar: se te propone actualizar sobre la tasa de excedentes
- Si ya está en el nivel máximo: alerta de que los excedentes están activos y cuándo resetea el límite

#### Notificaciones de restablecimiento de uso

Al inicio de cada ciclo de facturación:
- **Sin excedentes:** Alerta con la cantidad de créditos disponibles
- **Con excedentes:** Alerta de créditos disponibles + commit de excedentes activos

---

### Administrar las preferencias de notificación

Las notificaciones de facturación están habilitadas por defecto. Para deshabilitarlas:

1. `Cmd/Ctrl + Mayús + P` → **Paleta de comandos**
2. Buscá **Notificaciones: Facturación**
3. Desmarca la opción para deshabilitar notificaciones de facturación

---

### Comprender sus patrones de uso

Las notificaciones proactivas te ayudan a:

- **Identificar picos de uso** — Entender cuándo y por qué aumenta tu consumo
- **Elegir el plan correcto** — Determinar si necesita actualizar o bajar de categoría
- **Optimizar flujos de trabajo** — Ajustar patrones de desarrollo para usar créditos eficientemente
- **Evitar sorpresas** — Estar informado sobre posibles cargos de overage antes de que ocurran

> 💡 Si recibes alertas de 80% de uso temprano en tu ciclo de facturación, considerarás actualizar a un nivel superior.

---

*📂 Capítulo: **Billing for individuals > Managing your taxes***

## Administrar sus impuestos

> **Fuente:** [kiro.dev/docs/billing/managing/](https://kiro.dev/docs/billing/managing/#accessing-your-billing-information)

---

La información de impuestos se gestiona desde el tablero de facturación.

### Actualización de información fiscal

1. En Kiro, selecciona el ícono de perfil
2. Elegí **Manage Plan** — serás redirigido al navegador
3. En la sección **Información de facturación** del tablero, podés:
   - Actualizar tu dirección de facturación
   - Agregar o actualizar tu **Identificación fiscal** (si aplica)

> ℹ️ Los cambios en la información de facturación se aplican solo para **facturas futuras**.

---

### Cumplimiento tributario

- Los impuestos aplicables varían según tu país o región de facturación.
- Kiro procesa pagos en USD a través de Stripe / Amazon Web Services, Inc.
- Para obtener más información sobre impuestos específicos de su región, comuníquese con [Soporte de facturación] (https://app.kiro.dev/account/usage?support_form)

---

*📂 Capítulo: **Billing for individuals > Contacting billing support***

## Cómo ponerse en contacto con el soporte de facturación

> **Fuente:** [kiro.dev](https://app.kiro.dev/account/usage?support_form)

---

Para problemas relacionados con facturación, pagos o suscripciones:

### Portal de soporte de facturación

Accedé al formulario de soporte de facturación directamente desde:
- [app.kiro.dev/account/usage?support_form](https://app.kiro.dev/account/usage?support_form)

O desde dentro de Kiro:
1. Seleccione el ícono de perfil
2. Busque la opción **Soporte de facturación** o **Contactar con soporte**

---

### Cómo encontrar su ID de usuario

Para incluir su ID de usuario en el ticket de soporte:

1. Abra el **panel de uso** en Kiro
2. Tu ID de usuario se muestra junto a tu correo electrónico y método de inicio de sesión
3. Busque la etiqueta **"User ID"** con un ícono de copia para copiarlo fácilmente

---

### Otros canales de soporte

| Canal | Uso |
|---|---|
| [Informar un error](https://github.com/kirodotdev/Kiro/issues/new/choose) | Reportar errores técnicos |
| [Sugerir una idea](https://github.com/kirodotdev/Kiro/issues/new?template=feature_request.yml) | Proponer nuevas características |
| [Formulario de soporte de facturación](https://app.kiro.dev/account/usage?support_form) | Problemas de facturación y pagos |

---

*📂 Capítulo: **Billing for individuals > Deleting your account***

## Eliminar tu cuenta

![Eliminar cuenta](https://kiro.dev/videos/delete-account.mp4)

> **Fuente:** [kiro.dev/docs/billing/deleting-account/](https://kiro.dev/docs/billing/deleting-account/)

---

Eliminar tu cuenta de Kiro permanentemente eliminará todas tus configuraciones personalizadas y cancelará cualquier suscripción activa. **Esta acción no se puede deshacer.**

### Pasos

1. En Kiro, abre la paleta de comandos:
   - **Mac:** `Cmd + Mayús + P`
   - **Windows/Linux:** `Ctrl + Mayús + P`
2. Busca **`> Kiro: Eliminar cuenta`** y seleccionalo
3. Confirmá la eliminación

---

### Ventana de recuperación de cuenta

Tenés **30 días** para restaurar tu cuenta:

- Durante ese período, simplemente volvé a iniciar sesión en Kiro
- Deberás saldar cualquier saldo pendiente antes de volver a aviones pagos
- Después de los 30 días sin iniciar sesión, la cuenta y todos los datos se eliminan **permanentemente**

---

*📂 Capítulo: **Billing for individuals > Related questions***

## Preguntas relacionadas

> **Fuente:** [kiro.dev/docs/billing/ related-questions/](https://kiro.dev/docs/billing/ related-questions/)

---

### ¿Qué es un crédito?

Un crédito es una unidad de trabajo en respuesta a avisos de usuario. Los créditos se miden al segundo decimal (mínimo 0.01 créditos por tarea).

| Tipo de tarea | Consumo estimado |
|---|---|
| Indicaciones simples | Menos de 1 crédito |
| Tareas complejas (Ejecución Spec) | Más de 1 crédito |
| Auto (modelo predeterminado) | Base X |
| Soneto 4 | 1.3X (30% más que Auto) |

---

### ¿Cuándo me factura Kiro?

Kiro factura en base a mes calendario (UTC). Los actualizaciones a mitad de mes se facturan inmediatamente con la diferencia prorrateada. Los excedentes aparecen como artículos separados en la factura mensual.

---

### ¿Qué pasa cuando llego al límite mensual?

- **Kiro Free:** Las solicitudes se pausan hasta el próximo mes. No hay excedentes disponibles: podés actualizar para acceso inmediato.
- **Pagos de aviones:** Si los excedentes están habilitados, continúa trabajando. Si no, las solicitudes se pausan. Podés actualizar en cualquier momento para acceso inmediato.

---

### ¿Cómo funciona el prorrateo?

**Primera vez que actualizas (Gratis → Pagado):**
- Carga prorratada por los días restantes del mes
- Acceso inmediato a los créditos completos del plan
- Si actualizas de nuevo el mismo mes: se descuenta lo ya pagado y se cobra la diferencia prorrateada

**Actualizaciones posteriores (Pagadas → Mejor pagadas):**
- Cargo retroactivo por la diferencia de precio para todo el mes
- El uso del mes se recalcula bajo los límites del nuevo plan (podés evitar excedentes retroactivamente)

---

### ¿Qué sucede con los créditos de bonificación si actualizo antes?

Si estás dentro del período de prueba de 30 días con créditos bonus, esos créditos se transferirán al plan nuevo por el resto del período de 30 días.

---

### Cerca de fin de mes: ¿actualizar o habilitar el excedente?

- Si solo quedan pocos días, activar excedentes suele ser más simple
- Si el costo acumulado de excedentes se acerca a la diferencia de precio del siguiente plan, considere actualizar
- En el primer mes pago, si actualizas tarde, se aplica descuento por lo ya pagado

---

### ¿Por qué una sola acción podría costar más de un crédito?

Algunos contextos son muy grandes (bases de código extensas, tareas muy complejas), superando el límite de tokens de una sola solicitud. Kiro lo cuenta como más de un crédito y muestra el total inmediatamente después de la interacción.

---

### ¿Cómo optimiza Kiro los costes?

Kiro reusar contexto donde sea posible y eficiencias de aplicaciones como almacenamiento en caché rápido y uso eficiente de herramientas de token. Pagás por request, no por token, y las ganancias de eficiencia se reflejan en el diseño de precios.

---

### ¿Qué países admiten planes pagos?

Kiro actualmente soporta facturación en la mayoría de los países. Consulta la [lista completa en la documentación oficial](https://kiro.dev/docs/billing/ related-questions/#what-countries-or-regions-are-supported-for-paid-plans). Se agregarán más países regularmente.

---

### ¿Cómo puedo recuperar mi ID de usuario?

![Identificación de usuario](https://kiro.dev/videos/user-id.mp4)

Tu ID de usuario está disponible en el **panel de uso**. Aparece junto a tu correo electrónico y método de inicio de sesión, con un ícono de copia para copiarlo fácilmente.

---

*📂 Capítulo: **Troubleshooting***

## Solución de problemas

> **Fuente:** [kiro.dev/docs/troubleshooting/](https://kiro.dev/docs/troubleshooting/)

---

### Problemas de instalación de Kiro

#### macOS: "Kiro está dañado y no se puede abrir"

Esta ventana emergente es un **falso positivo** en las funciones de seguridad de macOS (Gatekeeper).

**Soluciones (pruebe en orden):**

1. Vaya a **Configuración del sistema → Privacidad y seguridad** y haga clic en **Permitir** o **Abrir de todos modos** para Kiro.
2. Arrastre `Kiro.app` a su escritorio, luego arrástrelo nuevamente a la carpeta Aplicaciones.
3. Reinicie su computadora.
4. Abra Terminal y ejecute:
   ```golpecito
   sudo xattr -d com.apple.quarantine /Aplicaciones/Kiro.app
   ```

---

### Problemas de autenticación

#### Fallos de redireccionamiento del navegador durante la autenticación

Si Kiro no te redirige a un navegador durante la autenticación:

**macOS:**
1. Abra Kiro → **Ayuda → Alternar herramientas de desarrollador**
2. Navegue a la pestaña **Consola**
3. Observe cualquier error durante el proceso de inicio de sesión.
4. Verifique que `ioreg` esté en su RUTA:
   ```golpecito
   eco $ RUTA
   cual ioreg
   # Si falta, normalmente se encuentra en /usr/sbin/ioreg
   ```

**Windows:**
1. Abra el símbolo del sistema como administrador
2. Ejecute Kiro con registro:
   ```
   C:\ruta\a\app.exe --enable-logging
   ```
3. Verifique los registros para detectar errores de acceso denegado: asegúrese de que su usuario tenga permisos de administrador

#### Problemas del Centro de identidad de AWS IAM

**Se requiere suscripción Q Developer Pro:**
Si ve *"Hubo un error al iniciar sesión"*, asegúrese de tener una suscripción **Q Developer Pro** válida. [Ver estado de suscripción →](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-admin-setup-subscribe-general.html)

**Limitaciones regionales:**
Kiro utiliza de forma predeterminada **Este de EE. UU. (Norte de Virginia)** para la autenticación del Centro de identidad. Si su perfil de Q Developer se encuentra en una región diferente, inicie sesión con Builder ID, Google o GitHub.

**Duración de la sesión y tiempos de espera:**
Las sesiones de Identity Center tienen un tiempo de espera predeterminado de **8 horas**. Los administradores pueden configurar tiempos de espera de sesión más largos en [documentación de AWS →](https://docs.aws.amazon.com/singlesignon/latest/userguide/user-session-duration-how-to-configure.html)

---

### Problemas de integración de Shell

#### Solución rápida: "Integración de Shell no disponible"

1. **Actualizar Kiro:** `Cmd+Shift+P` / `Ctrl+Shift+P` → `Kiro: buscar actualizaciones`
2. **Habilitar integración:** `Cmd+Shift+P` / `Ctrl+Shift+P` → `Kiro: Habilitar integración de Shell`
3. **Reiniciar** Kiro

#### Instalación manual

Si la configuración automática falla, agregue a su configuración de shell:

**Zsh (`~/.zshrc`):**
```golpecito
[[ "$TERM_PROGRAM" == "kiro" ]] && . "$(kiro --locate-shell-integration-path zsh)"
```

**Bash (`~/.bashrc`):**
```golpecito
[[ "$TERM_PROGRAM" == "kiro" ]] && . "$(kiro --locate-shell-integration-path bash)"
```

**Pescado (`~/.config/fish/config.fish`):**
```pescado
coincidencia de cadena -q "$TERM_PROGRAM" "kiro" y . (kiro --locate-shell-integration-path pez)
```

**PowerShell ($Perfil):**
```powershell
si ($env:TERM_PROGRAM -eq "kiro") { . "$(kiro --locate-shell-integration-path pwsh)" }
```

#### Kiro se atasca en el estado "Trabajando..." / Salida del terminal no visible

Causado por personalizaciones del shell que interfieren con la integración del terminal (por ejemplo, `bash-it`, `Oh My Posh`, `Powerlevel10k`).

**Usuarios de Powerlevel10k** — Agregar a `~/.p10k.zsh`:
```golpecito
tipografía -g POWERLEVEL9K_TERM_SHELL_INTEGRATION=true
```

O deshabilite las personalizaciones solo cuando se ejecute dentro de Kiro (`~/.zshrc`):
```golpecito
if [[ "$TERM_PROGRAM" == "kiro" ]]; entonces
  # Dejar vacío
otra cosa
  ZSH_THEME="nivel de potencia10k/nivel de potencia10k"
fi
```

**Usuarios de conchas de pescado** — Actualice el script de integración de conchas para incluir `"kiro"`:

Archivo: `/Applications/Kiro.app/Contents/Resources/app/out/vs/workbench/contrib/terminal/common/scripts/shellIntegration.fish`

Cambiar:
```
coincidencia de cadena --quiet "$TERM_PROGRAM" "vscode"
```
Para:
```
coincidencia de cadena --quiet "$TERM_PROGRAM" "vscode" "kiro"
```

---

### Problemas de Windows

#### Actualizaciones deshabilitadas debido a la instalación del administrador

Si Kiro fue instalado por un administrador, es posible que las actualizaciones automáticas estén deshabilitadas. Reinstale Kiro como usuario habitual para restaurar las actualizaciones automáticas.

#### No se pueden ejecutar scripts

Habilite la política de ejecución de PowerShell:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

#### Problema de ruta de OneDrive

Si su perfil de usuario está almacenado en OneDrive, Kiro puede tener dificultades con la resolución de rutas. Mueva su espacio de trabajo de Kiro a una ruta local (fuera de OneDrive) para resolverlo.

---

### Problemas de conexión del servidor MCP

#### Problemas comunes

1. **Verificar el estado del servidor** — Abra el panel Kiro → pestaña Servidores MCP → verifique el indicador de estado de la conexión
2. **Verificar configuración**: asegúrese de que `mcp.json` tenga una sintaxis válida y que los comandos/argumentos del servidor sean correctos.
3. **Verifique los requisitos previos**: para el servidor de documentación de AWS, verifique que Python 3.10+ y `uv` estén instalados.
4. **Revisar registros** — Panel de salida → seleccione **"Kiro - Registros de MCP"** en el menú desplegable

#### Servidor de documentación de AWS

```golpecito
## Verificar la instalación ultravioleta
uv --versión

## Verificar la versión de Python (se requiere 3.10+)
python3 --versión
```

---

### Obtener ayuda

- [Problemas de GitHub →](https://github.com/kirodotdev)
- [Documentación oficial →](https://kiro.dev/docs/)

---

*📂 Capítulo: **Enterprise > Concepts***

## Conceptos empresariales

> **Fuente:** [kiro.dev/docs/enterprise/concepts/](https://kiro.dev/docs/enterprise/concepts/)

---

Glosario de términos clave para administradores que gestionan suscripciones y usuarios de Kiro Enterprise.

---

### Referencia de conceptos

| Término | Definición |
|---|---|
| **Centro de identidad de AWS IAM** | Servicio AWS que proporciona un lugar central para gestionar las identidades de usuarios de Kiro |
| **Región de AWS** | Ubicación física donde AWS agrupa sus centros de datos. Relevante en dos dimensiones: (1) región donde está habilitado IAM Identity Center, y (2) región donde se crea el perfil de Kiro (donde se almacenan los datos) |
| **Grupo** | Colección de usuarios dentro de IAM Identity Center. Al suscribir un grupo a Kiro, los usuarios individuales se suscriben por separado (no existe concepto de suscripción grupal) |
| **Consola Kiro** | Consola dentro de la consola AWS donde crearás y gestionarás suscripciones Kiro y configurarás ajustes. Aparece como "Kiro" en el menú desplegable de servicios AWS |
| **Créditos de Kiro** | Unidad de consumo que mide el uso de las características de IA de Kiro. Se gastan en interacciones con IA y se reponen según el nivel de suscripción |
| **Usuario empresarial de Kiro** | Usuario que fue agregado y suscrito a un nivel de Kiro a través de la consola AWS, con acceso mediante IAM Identity Center, Okta o Microsoft Entra ID |
| **Perfil de Kiro** | Abstracción de gestión que define y aplicaciones configuraciones administrativas y suscripciones a usuarios empresariales en una cuenta AWS y región determinadas. Una cuenta AWS + región = un único perfil. Se configura desde la consola Kiro |
| **Nivel de suscripción de Kiro** | Plan de precios con una cantidad predeterminada de créditos Kiro (Free, Pro, Pro+, Power) |

---

*📂 Capítulo: **Enterprise > Onboarding quickstart***

## Inicio rápido de incorporación

> **Fuente:** [kiro.dev/docs/enterprise/getting-started/](https://kiro.dev/docs/enterprise/getting-started/)

---

Esta guía está dirigida a **administradores** que quieren incorporar a su equipo en Kiro y gestionar sus suscripciones.

---

### Pasos para incorporar a su equipo

1. **Crear una cuenta AWS** (si no tienes una)
   - [Crear cuenta AWS →](https://docs.aws.amazon.com/accounts/latest/reference/manage-acct-creating.html)

2. **Iniciar sesión en AWS**
   - Como usuario root de AWS o usuario con rol privilegiado
   - Alternativamente, configurará un [administrador con permisos mínimos](https://kiro.dev/docs/enterprise/iam/#policy-allow-administrators-to-configure-kiro-and-subscribe-users)

3. **Conectar tu proveedor de identidad**
   - Agregue usuarios desde AWS IAM Identity Center, o conecte un IdP externo (Okta o Microsoft Entra ID)
   - [Guía de Proveedor de Identidad →](./03_Connecting%20your%20identity%20provider.md)

4. **Crear un perfil de Kiro y suscribir usuarios**
   - En la consola AWS, navegá a la **consola Kiro**
   - Crea un perfil y suscribete usuarios/grupos
   - [Guía de suscripción →](./04_Subscribe%20your%20team.md)

5. **Los usuarios recibirán un correo electrónico**
   - Dentro de las 24 horas, los usuarios suscritos reciben instrucciones de descarga e inicio de sesión para Kiro IDE y Kiro CLI.
   - Alternativamente pueden descargar desde [kiro.dev](https://kiro.dev/)

---

*📂 Capítulo: **Enterprise > Connecting your identity provider***

## Conectando su proveedor de identidad

> **Fuente:** [kiro.dev/docs/enterprise/identity-provider/](https://kiro.dev/docs/enterprise/identity-provider/)

---

Kiro soporta conectar su proveedor de identidad directamente o a través de AWS IAM Identity Center.

---

### Fuentes de identidad admitidas

| Opción | Descripción |
|---|---|
| **Centro de identidad de AWS IAM** | Gestión de identidades centralizadas directamente en AWS |
| **Okta** (IdP directo) | Conecta Okta directamente a Kiro |
| **ID de Microsoft Entra** (IDP directo) | Conecte Microsoft Entra ID directamente a Kiro |

---

### Opción 1: Centro de identidad de AWS IAM

Consultor [guía de IAM Identity Center →](https://kiro.dev/docs/enterprise/identity-provider/iam-identity-center)

> **Recomendación:** Utilice AWS Organizations al configurar IAM Identity Center para habilitar una instancia de organización con gestión centralizada de identidades en múltiples cuentas AWS.
> ⚠️ Las instancias de cuenta individual **no pueden** actualizarse a instancias de organización — requieren eliminación y recreación.

---

### Opción 2: Proveedor de identidad externo (directo)

#### Okta
Consultar [guía de configuración de Okta →](https://kiro.dev/docs/enterprise/identity-provider/okta)

#### Identificación de Microsoft Entra
Consultar [Guía de configuración de Microsoft Entra ID →](https://kiro.dev/docs/enterprise/identity-provider/microsoft-entra)

---

### Próximos pasos

Una vez conectado el proveedor de identidad, podrás suscribir usuarios esos o grupos a Kiro:
- [Suscribe tu equipo →](./04_Subscribe%20your%20team.md)

---

*📂 Capítulo: **Enterprise > Subscribe your team***

## Suscríbete a tu equipo

> **Fuente:** [kiro.dev/docs/enterprise/subscribe/](https://kiro.dev/docs/enterprise/subscribe/)

---

### Requisitos previos

Antes de comenzar, asegúrese de tener:

- **Cuenta AWS** — [Crear cuenta →](https://docs.aws.amazon.com/accounts/latest/reference/manage-acct-creating.html)
- **Permisos AWS** — Como administrador de Kiro, necesitas acceder a la consola de Kiro. Ver [permisos mínimos necesarios →](https://kiro.dev/docs/enterprise/iam/#policy-allow-administrators-to-configure-kiro-and-subscribe-users)
- **Proveedor de identidad configurado** — IAM Identity Center, Okta o Microsoft Entra ID con los usuarios que quieren suscribirse
- **Usuarios y grupos** — Desde el directorio del IdP o de un IdP externo conectado a IAM Identity Center

---

### Crea el perfil de Kiro

![Suscribirse Crear perfil de Kiro](https://kiro.dev/videos/docs/enterprise/subscribe-create-kiro-profile.mp4)

1. Iniciá sesión en la **AWS Management Console**
2. Cambiá a la **consola Kiro**
3. Verifica que estás en la [región AWS soportada](https://kiro.dev/docs/enterprise/supported-regions) donde quieres crear el perfil de Kiro
4. Elegí el botón **Regístrese en Kiro**
5. Revisá el contenido del diálogo y elige **Enable** — el perfil de Kiro se crea
6. (Opcional) Edite el perfil con un nombre o descripción diferente desde la página de Configuración

---

### Suscríbete a tu equipo a Kiro

![Suscribirse Agregar usuario](https://kiro.dev/videos/docs/enterprise/subscribe-add-user.mp4)

1. Cambiá a la **consola Kiro**
2. Verifica que estás en la región AWS donde creaste el perfil de Kiro
3. En la página **Usuarios y Grupos**, elija la pestaña **Usuarios** o **Grupos**
4. Elija el botón **Agregar usuario** o **Agregar grupo** — aparece un diálogo para seleccionar el nivel de suscripción
5. Elija el nivel deseado (Pro, Pro+, Power) y seleccione **Continuar**
6. En la barra de búsqueda, busca el grupo o usuario que querrás suscribirse
7. Los usuarios/grupos se autocompletan desde tu Identity Provider
8. Seleccioná y elegí **Assign** — los usuarios/grupos quedan suscriptos

---

### ¿Qué pasa después?

- Los usuarios suscritos reciben un correo electrónico dentro de las **24 horas** con instrucciones de descarga e inicio de sesión
- Podés gestionar suscripciones desde [Gestionar suscripciones →](./05_Manage%20subscriptions.md)

---

*📂 Capítulo: **Enterprise > Manage subscriptions***

## Administrar suscripciones

> **Fuente:** [kiro.dev/docs/enterprise/subscription-management/](https://kiro.dev/docs/enterprise/subscription-management/)

---

### Cambiar los planes de suscripción de Kiro

![Administrar suscripción Cambiar suscripción](https://kiro.dev/videos/docs/enterprise/manage-subscription-change-subscription.mp4)

1. Iniciá sesión en la **AWS Management Console**
2. Cambiá a la **consola Kiro**
3. En la página **Usuarios y Grupos**, elija la pestaña correspondiente
4. Seleccione el usuario o grupo cuya suscripción quiera cambiar
5. Elegí **Change plan** y seleccioná el nuevo plan → **Continuar**

> - **Actualizaciones:** Efectivos de forma inmediata
> - **Downgrades:** Efectivos al inicio del mes siguiente

---

### Darse de baja de usuarios de Kiro

![Administrar suscripción Desactivar usuario](https://kiro.dev/videos/docs/enterprise/manage-subscription-deactivate-user.mp4)

1. En la **consola Kiro**, ve a **Usuarios y Grupos**
2. Selecciona el usuario o grupo a desuscribir
3. Elegí **Desactivar plan** → revisá el diálogo y elegí **Cancelar suscripción**

Los usuarios desuscriptos pierden acceso **de manera inmediata** a las características pagas de Kiro.

---

### Habilitar excedentes para usuarios de Kiro

Los excedentes permiten a los usuarios continuar trabajando para superar los límites de su plan. Por defecto están **deshabilitados**. Al habilitarse, aplique a **todos los usuarios del perfil**.

1. En la **consola Kiro**, elige **Configuración**
2. Busca la sección **Kiro settings**
3. Activá **Excedentes**

> ℹ️ La configuración de gorras personalizadas para excedentes no está disponible aún (próximamente).

---

### Estados de suscripción

| Estado | Descripción |
|---|---|
| **Activo** | El usuario está suscripto. Se te cobra por la suscripción |
| **Cancelado** | Suscripción cancelada por un administrador. Sin acceso a características pagas |
| **Pendiente** | Suscripto pero no activó la suscripción. No se cobra; sin datos en la columna "Último activo" |

> Los grupos no tienen estados propios — las suscripciones se asignan a usuarios individuales.

---

*📂 Capítulo: **Enterprise > Governance***

## Gobernanza

> **Fuente:** [kiro.dev/docs/enterprise/governance/](https://kiro.dev/docs/enterprise/governance/)

---

Como administrador, podrás controlar qué modelos y servidores MCP están disponibles para tus usuarios. Los controles de gobierno se gestionan desde la **Consola Kiro → Configuración → Configuración compartida**.

---

### Gobernanza modelo

Por defecto, los usuarios pueden acceder a cualquier modelo soportado por Kiro.

**Opciones de control:**
- **Activar gestión de acceso a modelos** → seleccioná una lista aprobada de modelos
- **Establecer un modelo por defecto** → se aplica automáticamente a todos los clientes

Para detalles: [kiro.dev/docs/enterprise/governance/model](https://kiro.dev/docs/enterprise/governance/model)

---

### Gobernanza del MCP

Por defecto, los usuarios pueden usar cualquier servidor MCP en su cliente Kiro.

**Opciones de control:**
- **Deshabilitar MCP completamente** para todos los usuarios del perfil
- **Especificar una lista permitida** de servidores MCP validados a través de un registro MCP

Estas políticas pueden configurarse a nivel de organización o sobreescribirse por cuenta.

Para detalles: [kiro.dev/docs/enterprise/governance/mcp](https://kiro.dev/docs/enterprise/governance/mcp)

---

*📂 Capítulo: **Enterprise > Monitor and track***

## Monitorear y rastrear

> **Fuente:** [kiro.dev/docs/enterprise/monitor-and-track/](https://kiro.dev/docs/enterprise/monitor-and-track/)

---

El monitoreo es una parte importante del mantenimiento de la confiabilidad, disponibilidad y rendimiento de Kiro para su organización.

---

### Monitoreo incorporado de Kiro

| Característica | Descripción | Más información |
|---|---|---|
| **Panel** | Métricas agregadas de actividad de usuarios suscritos | [Ver el uso de Kiro en el panel →](https://kiro.dev/docs/enterprise/monitor-and-track/dashboard) |
| **Informes de actividad del usuario** | Actividad individual de cada usuario en Kiro | [Ver actividad por usuario →](https://kiro.dev/docs/enterprise/monitor-and-track/user-activity) |
| **Registros rápidos** | Registro de todos los avisos que los usuarios ingresan en el chat de Kiro | [Registrar las indicaciones de los usuarios →](https://kiro.dev/docs/enterprise/monitor-and-track/prompt-logging) |

---

### Herramientas de monitoreo de AWS

| Herramienta | Uso |
|---|---|
| **AWS Cloud Trail** | Captura llamadas a la API y eventos relacionados; registre qué usuarios llamaron a AWS, desde qué IP y cuándo |
| **Amazon CloudWatch** | Monitorea recursos AWS en tiempo real; creará tableros personalizados, alarmas y rastreá métricas como número de invocaciones de Kiro o usuarios activos diarios |

---

*📂 Capítulo: **Enterprise > Settings***

## Configuración empresarial

> **Fuente:** [kiro.dev/docs/enterprise/settings/](https://kiro.dev/docs/enterprise/settings/)

---

Un administrador puede controlar las siguientes configuraciones dentro de un **perfil de Kiro**.

---

### Configuraciones disponibles

| Configuración | Descripción | Más información |
|---|---|---|
| **Cifrado en reposo** | Configurar el cifrado de datos en reposo | [Protección de datos →](https://kiro.dev/docs/privacy-and-security/data-protection#encryption-at-rest) |
| **Panel de uso** | Visualización del uso agregado de Kiro | [Ver uso →](https://kiro.dev/docs/enterprise/monitor-and-track/dashboard) |
| **Actividad por usuario** | Informe de actividad individual por usuario | [Ver actividad →](https://kiro.dev/docs/enterprise/monitor-and-track/user-activity) |
| **Registro rápido** | Registro de todos los avisos de usuarios | [Indicaciones de registro →](https://kiro.dev/docs/enterprise/monitor-and-track/prompt-logging) |
| **Excedentes** | Habilitá overages para todos los usuarios del perfil | [Gestión de excedentes →](https://kiro.dev/docs/enterprise/subscription-management#enabling-overages-for-kiro-users) |
| **Herramientas web** | Controlá si los usuarios pueden usar `web_search` y `web_fetch` | Ver abajo |

---

### Configuración de herramientas web

Controla si los usuarios pueden usar las herramientas de acceso web (`web_search` y `web_fetch`).

**Para deshabilitar el acceso web para todos los usuarios:**

1. Abrí la **consola Kiro**
2. Elegí **Ajustes**
3. En **Configuración compartida**, desactiva **Herramientas de búsqueda y recuperación web**

> Cuando las herramientas web están deshabilitadas, los usuarios verán una notificación en `/tools` indicando que el acceso web fue deshabilitado por su administrador.

---

*📂 Capítulo: **Enterprise > Billing***

## Facturación empresarial

> **Fuente:** [kiro.dev/docs/enterprise/billing/](https://kiro.dev/docs/enterprise/billing/)

---

### Comparación de niveles

La facturación Enterprise es mensual por usuario suscrito. Para ver el detalle de precios por nivel: [kiro.dev/pricing/](https://kiro.dev/pricing/)

> Los planos y métodos de pago también se aplican a regiones **AWS GovCloud (US)**.

---

### Consideraciones de prorrateo

| Situación | Comportamiento |
|---|---|
| **Nueva suscripción a mitad de mes** | Carga prorrateada; acceso inmediato a los créditos completos del nivel |
| **Descripción mitad de mes** | Se paga el mes completo; la cancelación toma efecto el próximo mes |
| **Actualización a mitad de mes** | Reembolso del nivel inferior + carga completa del nivel superior. El mes se recalcula bajo los límites del nuevo nivel |
| **Rebaja de categoría a mitad de mes** | Se paga completo el nivel superior; el nivel inferior aplica desde el próximo mes |

> Actualizaciones → inmediatos. Degradaciones → inicio del siguiente mes.

---

### ¿Me facturarán dos veces?

**Perfil de Mismo Kiro:** Si un usuario está suscrito en dos grupos del mismo perfil, **no** se factura dos veces. Se paga el nivel más alto asignado al usuario.

**Diferente perfil de Kiro:** Si un usuario está suscrito en dos perfiles distintos (ej. dos regiones AWS diferentes), **sí** se factura dos veces.

---

### Ver su factura

- **AWS Billing and Cost Management** → pestaña **Cargos por servicio** → sección **Kiro**
- Para identificar costos por usuario: en **Exportaciones de datos**, creará una exportación con la opción **Incluir ID de recursos** activada

Recursos:
- [¿Qué es la gestión de costos y facturación de AWS? →](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-what-is.html)
- [Creación de exportaciones de datos →](https://docs.aws.amazon.com/cur/latest/userguide/dataexports-create.html)

---

*📂 Capítulo: **Enterprise > IAM***

## IAM: gestión de identidad y acceso

> **Fuente:** [kiro.dev/docs/enterprise/iam/](https://kiro.dev/docs/enterprise/iam/)

---

### Políticas basadas en la identidad para Kiro

Para que un administrador pueda gestionar Kiro desde la consola de AWS (suscribir usuarios, configurar la integración con IAM Identity Center y AWS Organizations, gestionar la configuración), necesita la siguiente política IAM mínima:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "sso:ListInstances", "sso:CreateInstance", "sso:CreateApplication",
        "sso:PutApplicationAuthenticationMethod", "sso:PutApplicationGrant",
        "sso:ListApplications", "sso:DescribeInstance", "sso:DescribeApplication",
        "sso:DeleteApplication", "sso:CreateApplicationAssignment",
        "sso:DeleteApplicationAssignment", "sso:UpdateApplication",
        "sso:DescribeRegisteredRegions", "sso:GetSSOStatus"
      ],
      "Resource": ["*"]
    },
    {
      "Effect": "Allow",
      "Action": [
        "user-subscriptions:ListClaims", "user-subscriptions:CreateClaim",
        "user-subscriptions:DeleteClaim", "user-subscriptions:UpdateClaim",
        "user-subscriptions:SetOverageConfig"
      ],
      "Resource": ["*"]
    },
    {
      "Effect": "Allow",
      "Action": [
        "codewhisperer:UpdateProfile", "codewhisperer:ListProfiles",
        "codewhisperer:CreateProfile"
      ],
      "Resource": ["*"]
    },
    {
      "Effect": "Allow",
      "Action": ["q:ListDashboardMetrics", "q:CreateAssignment", "q:DeleteAssignment"],
      "Resource": ["*"]
    },
    {
      "Effect": "Allow",
      "Action": ["cloudwatch:GetMetricData", "cloudwatch:ListMetrics"],
      "Resource": ["*"]
    }
  ]
}
```

> La política completa también incluye permisos para `iam`, `identitystore`, `sso-directory`, `organizations`, `kms` y `signin`. Ver [documentación completa →](https://kiro.dev/docs/enterprise/iam/#policy-allow-administrators-to-configure-kiro-and-subscribe-users)

---

### Roles vinculados al servicio

Kiro usa los siguientes roles vinculados a servicios de AWS:

| papel | Propósito |
|---|---|
| `AWSServiceRoleForUserSubscriptions` | Gestión de suscripciones de usuarios |
| `AWSServiceRoleForAmazonQDeveloper` | Integración con Amazon Q Developer |

---

*📂 Capítulo: **Enterprise > Supported regions***

## Regiones admitidas

> **Fuente:** [kiro.dev/docs/enterprise/supported-regions/](https://kiro.dev/docs/enterprise/supported-regions/)

---

### Regiones de la consola Kiro y del perfil Kiro

Las siguientes regiones soportan la consola Kiro y la creación de perfiles Kiro:

| Región |
|---|
| Este de EE. UU. (Norte de Virginia) |
| Europa (Fráncfort) |
| AWS GovCloud (EE.UU.-Este) |
| AWS GovCloud (EE.UU.-Oeste) |

---

### Regiones del Centro de identidad de IAM respaldadas por Kiro

Los usuarios a suscribirse deben tener identidades en una instancia de IAM Identity Center (o IdP conectado) en alguna de las siguientes regiones:

| Región | Código |
|---|---|
| Este de EE. UU. (Ohio) | `nosotros-este-2` |
| Este de EE. UU. (Norte de Virginia) | `nosotros-este-1` |
| Oeste de EE. UU. (Norte de California) | `nosotros-oeste-1` |
| Oeste de EE. UU. (Oregón) | `nosotros-oeste-2` |
| Asia Pacífico (Bombay) | `ap-sur-1` |
| Asia Pacífico (Osaka) | `ap-noreste-3` |
| Asia Pacífico (Seúl) | `ap-noreste-2` |
| Asia Pacífico (Singapur) | `ap-sureste-1` |
| Asia Pacífico (Sídney) | `ap-sureste-2` |
| Asia Pacífico (Tokio) | `ap-noreste-1` |
| Canadá (Centro) | `ca-central-1` |
| Europa (Fráncfort) | `eu-central-1` |
| Europa (Irlanda) | `ue-oeste-1` |
| Europa (Londres) | `eu-oeste-2` |
| Europa (París) | `ue-oeste-3` |
| Europa (Estocolmo) | `ue-norte-1` |
| América del Sur (São Paulo) | `sa-este-1` |
| AWS GovCloud (EE.UU.-Este) | `us-gov-este-1` |
| AWS GovCloud (EE.UU.-Oeste) | `us-gov-west-1` |

---

*📂 Capítulo: **MCP > Configuration***

## Protocolo de contexto modelo (MCP)

> **Fuente:** [kiro.dev/docs/mcp/](https://kiro.dev/docs/mcp/)

---

MCP es un protocolo que permite a Kiro comunicarse con servidores externos para acceder a herramientas, indicaciones y recursos especializados. Por ejemplo, el servidor MCP de documentación de AWS proporciona herramientas para buscar, leer y obtener recomendaciones de la documentación de AWS directamente dentro de Kiro.

Con MCP, puedes:
- Acceda a bases de conocimiento y documentación especializadas.
- Integrar con servicios externos y API.
- Amplíe las capacidades de Kiro con herramientas específicas de dominio
- Utilice plantillas de mensajes y plantillas de recursos proporcionadas por el servidor a través del sistema de menciones `#` en el chat.
- Responder a las solicitudes de obtención del servidor cuando las herramientas necesitan información adicional durante la ejecución.
- Cree herramientas personalizadas para sus flujos de trabajo específicos

---

### Configuración de MCP

#### Requisitos previos

Antes de usar MCP:
1. Asegúrate de tener instalada la última versión de Kiro.
2. Consulte la documentación de cada servidor MCP para conocer los requisitos previos específicos.

#### Habilitación del soporte MCP

Después de crear su archivo de configuración:
1. Abra Configuración con `Cmd+` (Mac) o `Ctrl+` (Windows/Linux)
2. Busque "MCP"
3. Habilite la configuración de soporte de MCP

#### Uso de la pestaña Servidores MCP

El panel Kiro incluye una **pestaña de servidores MCP** que muestra:
- Todos los servidores MCP configurados
- Indicadores de estado de conexión
- Acceso rápido a las herramientas del servidor.

Para utilizar esta función:
1. Selecciona el ícono de Kiro en la barra de actividades.
2. Navegue a la pestaña **Servidores MCP**
3. Haga clic en el nombre de cualquier herramienta para insertar un mensaje de marcador de posición en el chat.

---

### Configuración

Los archivos de configuración de MCP utilizan el formato JSON:

```json
{
  "mcpServers": {
    "local-server-name": {
      "command": "command-to-run-server",
      "args": ["arg1", "arg2"],
      "env": {
        "ENV_VAR1": "hard-coded-variable",
        "ENV_VAR2": "${EXPANDED_VARIABLE}"
      },
      "disabled": false,
      "autoApprove": ["tool_name1", "tool_name2"],
      "disabledTools": ["tool_name3"]
    },
    "remote-server-name": {
      "url": "https://endpoint.to.connect.to",
      "headers": {
        "HEADER1": "value1",
        "HEADER2": "value2"
      },
      "disabled": false,
      "autoApprove": ["tool_name1"],
      "disabledTools": ["tool_name3"]
    }
  }
}
```

#### Ubicaciones de configuración

| Nivel | Archivo | Alcance |
|---|---|---|
| **Espacio de trabajo** | `.kiro/settings/mcp.json` | Solo espacio de trabajo actual: ideal para servidores de proyectos específicos |
| **Usuario** | `~/.kiro/settings/mcp.json` | Todos los espacios de trabajo: lo mejor para servidores de uso frecuente |

> Si ambos archivos existen, las configuraciones se **fusionan** y la configuración del espacio de trabajo tiene prioridad.

#### Creando archivos de configuración

- **Paleta de comandos:** `Cmd+Shift+P` → buscar "MCP" → "Kiro: Configurar servidores MCP"
- **Panel Kiro:** Navegue a la pestaña de servidores MCP → haga clic en **+** para agregar un nuevo servidor

#### Variables de entorno

```json
{
  "mcpServers": {
    "server-name": {
      "env": {
        "API_KEY": "${YOUR_API_KEY}",
        "DEBUG": "true",
        "TIMEOUT": "30000"
      }
    }
  }
}
```

#### Deshabilitar servidores temporalmente

```json
{
  "mcpServers": {
    "server-name": {
      "disabled": true
    }
  }
}
```

#### Consideraciones de seguridad

- Utilice referencias de variables de entorno ("${API_TOKEN}`) en lugar de codificar valores sensibles
- Nunca envíe archivos de configuración con credenciales al control de versiones.
- Conéctese únicamente a servidores remotos confiables
- Revisar los permisos de la herramienta antes de agregarlos a "autoApprove".

---

### Solución de problemas

#### Problemas de configuración comunes

1. **Valide la sintaxis JSON**: asegúrese de que no haya errores de sintaxis, comas, comillas o corchetes faltantes.
2. **Verificar rutas de comando**: asegúrese de que el comando exista en su RUTA; intenta ejecutarlo directamente en tu terminal
3. **Verifique las variables de entorno**: verifique que las variables de entorno requeridas estén configuradas y tengan el nombre correcto
4. **Guardar cambios de configuración**: los cambios se aplican automáticamente al guardar (`Cmd+S`)

#### Comprobación de registros de MCP

1. Abre el panel de Kiro
2. Seleccione la pestaña **Salida**
3. Elija **"Kiro - Registros de MCP"** en el menú desplegable.

---

### Próximos pasos

- [Configuración de MCP →](https://kiro.dev/docs/mcp/configuration/)
- [Gestión del servidor MCP →](https://kiro.dev/docs/mcp/servers/)
- [Uso de herramientas MCP →](https://kiro.dev/docs/mcp/usage/)
- [Mejores prácticas / Seguridad →](https://kiro.dev/docs/mcp/security/)
- [Documentación oficial de MCP →](https://modelcontextprotocol.io/introduction)

---

*📂 Capítulo: **Guides > Migrating from VS Code***

## Guías

> **Fuente:** [kiro.dev/docs/guides/](https://kiro.dev/docs/guides/)

---

Guías oficiales paso a paso para aprender Kiro a través de escenarios prácticos.

---

### Guías disponibles

| Guía | Descripción |
|---|---|
| [Aprende jugando →](https://kiro.dev/docs/guides/learn-by-playing/) | Cree un proyecto de juego real mientras aprende las potentes funciones de Kiro a través de tutoriales interactivos prácticos |
| [Soporte de idiomas →](https://kiro.dev/docs/guides/languages-and-frameworks/) | Guías específicas del marco para React, Python, Go y más para ayudarlo a aprovechar Kiro al máximo con su pila tecnológica |
| [Migración desde VS Code →](https://kiro.dev/docs/guides/migrate-from-vscode/) | Realice una transición perfecta de VS Code a Kiro con una migración con un solo clic que incluye todas sus extensiones y configuraciones |

---

### Migrar desde VS Code

La base VS Code de Kiro permite una compatibilidad total con su entorno de desarrollo. Puede transferir su configuración personalizada (extensiones, temas, configuraciones y accesos directos) sin problemas de compatibilidad.

#### Migración de perfil

1. Abra la paleta de comandos: `Cmd+Shift+P` (Mac) / `Ctrl+Shift+P` (Windows/Linux)
2. Busque **"Importar perfil desde VS Code"**
3. Kiro detectará e importará automáticamente sus perfiles de VS Code

##### Migración manual de perfiles

Si la migración automática no funciona:
1. En VS Code: `Cmd+Shift+P` → "Perfiles: Exportar perfil" → guardar como `.code-profile`
2. En Kiro: `Cmd+Shift+P` → "Perfiles: Importar perfil" → seleccione el archivo

#### Configuración e interfaz

| Artículo | Cómo acceder |
|---|---|
| **Configuración de Kiro** | `Cmd/Ctrl+Shift+P` → "Preferencias: Abrir Configuración (UI)" → navegue a la sección Kiro Agent |
| **Configuración del código VS** | Misma ruta de la paleta de comandos: sus preferencias de VS Code existentes siguen siendo completamente funcionales |

Kiro amplía la arquitectura de configuración de VS Code con controles dedicados para:
- Comportamientos de IA y automatización de agentes.
- Comandos confiables
- Funciones exclusivas de Kiro (dirección, especificaciones, hooks)

#### Actualizaciones de versión

Kiro se mantiene sincronizado con el ciclo de desarrollo de VS Code mediante cambios de base regulares. Incorporamos las funciones más recientes y seleccionamos versiones estables de VS Code para garantizar la confiabilidad junto con mejoras de IA.

#### Compatibilidad de extensiones

Kiro utiliza el **registro de extensión OpenVSX**. Las extensiones disponibles en OpenVSX migran sin problemas:

| Tipo de extensión | Compatibilidad |
|---|---|
| Extensiones de idiomas | Funcionalidad completa para extensiones disponibles en OpenVSX |
| Extensiones de temas | Compatibilidad visual completa |
| Extensiones de depuración | Flujos de trabajo de depuración ininterrumpidos para extensiones compatibles |
| Extensiones de Git | Ampliado con generación de commit inteligente y revisión de código automatizada |

> ⚠️ Solo se pueden importar extensiones disponibles en el **registro OpenVSX**. Es posible que algunas exclusivas de VS Code Marketplace no estén disponibles en Kiro.

---

*📂 Capítulo: **Troubleshooting***

## Solución de problemas

> **Fuente:** [kiro.dev/docs/troubleshooting/](https://kiro.dev/docs/troubleshooting/)

---

### Problemas de instalación

#### macOS: "Kiro está dañado y no se puede abrir"

Este error es un falso positivo de las funciones de seguridad de macOS.

**Soluciones:**

1. Vaya a **Configuración del sistema → Privacidad y seguridad** → haga clic en **Permitir** o **Abrir de todos modos** para Kiro
2. Arrastrará `Kiro.app` al escritorio, luego arrastralo del escritorio a la carpeta Aplicaciones → reiniciará el sistema
3. Abrí la terminal y ejecutá:
   ```golpecito
   sudo xattr -d com.apple.quarantine /Aplicaciones/Kiro.app
   ```

---

### Problemas de autenticación

#### Fallos de redireccionamiento del navegador durante la autenticación

**Windows:**
1. Abra el símbolo del sistema como administrador
2. Ejecutá Kiro con logging habilitado:
   ```
   C:\ruta\a\app.exe --enable-logging
   ```
3. Revisá los logs en busca de errores
4. Si ves "acceso denegado", verificará que tu usuario tiene permisos de administrador

**macOS:**
1. Abrí Kiro → **Ayuda → Alternar herramientas de desarrollador**
2. Navegá a la pestaña **Consola**
3. Observará los errores durante el inicio de sesión
4. Problema común: comando `ioreg` faltante en el PATH:
   ```golpecito
   eco $ RUTA
   cual ioreg
   ```
   Si `ioreg` no aparece, generalmente está en `/usr/sbin/ioreg`

---

#### Problemas del Centro de identidad de AWS IAM

| Error | causa | Solución |
|---|---|---|
| `"Hubo un error al iniciar sesión"` | No tienes una suscripción Q Developer Pro activa | [Ver cómo activar Q Developer Pro →](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-admin-setup-subscribe-general.html) |
| No podés iniciar sesión a pesar de tener credenciales válidas | Limitación regional — Kiro solo soporta Identity Center en US East (N. Virginia) | Utilice Builder ID para iniciar sesión en redes sociales (Google, GitHub) |
| Sesión expira constantemente | Timeout por defecto de 8 horas | El administrador puede [configurar sesiones más largas →](https://docs.aws.amazon.com/singlesignon/latest/userguide/user-session-duration-how-to-configure.html) |

---

### Problemas de integración de Shell

La integración de shell conecta Kiro con tu terminal para ejecutar comandos automáticamente y procesar resultados. Sin ella, necesitarás copiar y pegar las salidas manualmente.

#### Solución rápida: "integración de shell no disponible"

1. Actualizá Kiro: `Cmd/Ctrl + Shift + P` → **Kiro: Buscar actualizaciones**
2. Habilitará la integración: `Cmd/Ctrl + Shift + P` → **Kiro: Habilitar integración de Shell**
3. Reinicia Kiro

#### Instalación manual

Si la configuración automática falla, agregue a su configuración de shell:

**Zsh (`~/.zshrc`):**
```golpecito
[[ "$TERM_PROGRAM" == "kiro" ]] && . "$(kiro --locate-shell-integration-path zsh)"
```

**Bash (`~/.bashrc`):**
```golpecito
[[ "$TERM_PROGRAM" == "kiro" ]] && . "$(kiro --locate-shell-integration-path bash)"
```

**Pescado (`~/.config/fish/config.fish`):**
```pescado
coincidencia de cadena -q "$TERM_PROGRAM" "kiro" y . (kiro --locate-shell-integration-path pez)
```

**PowerShell ($Perfil):**
```powershell
si ($env:TERM_PROGRAM -eq "kiro") { . "$(kiro --locate-shell-integration-path pwsh)" }
```

#### Kiro se atasca en "Trabajando..." en los comandos de la terminal

Causado por personalizaciones del shell que interfieren con la integración de terminal (ej. bash-it, Oh My Posh, Powerlevel10k).

**Usuarios de Powerlevel10k:** Agrega a tu `.p10k.zsh`:
```golpecito
tipografía -g POWERLEVEL9K_TERM_SHELL_INTEGRATION=true
```

O deshabilitará los temas dentro de Kiro (`.zshrc`):
```golpecito
if [[ "$TERM_PROGRAM" == "kiro" ]]; entonces
  # Dejar vacío
otra cosa
  ZSH_THEME="nivel de potencia10k/nivel de potencia10k"
fi
```

**Usuarios de conchas de pescado:** Editá el archivo de integración de Kiro:
```
/Aplicaciones/Kiro.app/Contents/Resources/app/out/vs/workbench/contrib/terminal/common/scripts/shellIntegration.fish
```
Cambiá la línea que verifica `"vscode"` para incluir también `"kiro"`:
```pescado
##Antes:
el estado es interactivo y la cadena coincide: silencioso "$TERM_PROGRAM" "vscode" y...
##Después:
el estado es interactivo y la cadena coincide: silencioso "$TERM_PROGRAM" "vscode" "kiro" y ...
```

---

### Problemas de Windows

#### Actualizaciones deshabilitadas debido a la instalación del administrador

Si ves este error:
```
Las actualizaciones están deshabilitadas porque está ejecutando la instalación de Kiro en el ámbito del usuario como administrador.
```

1. Haz clic en derecho en el ícono de Kiro → **Mostrar más opciones**
2. Seleccioná **Propiedades** → pestaña **Compatibilidad**
3. Desmarcar **Ejecuta este programa como administrador**
4. Haga clic en **Aplicar** → **Aceptar**

#### No se pueden ejecutar scripts (PowerShell 7+)

```powershell
## Verificar política actual
Get-ExecutionPolicy

## Establecer política
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

#### Problema de ruta de OneDrive

Si usa OneDrive en Windows y la ruta del escritorio causa problemas:

1. Abra el símbolo del sistema como administrador
2. Crea un enlace simbólico:
   ```
   mklink /J "C:\Users\<nombre de usuario>\Desktop" "C:\Users\<nombre de usuario>\OneDrive\Desktop"
   ```
3. Reiniciá el IDE

---

### Problemas de conexión del servidor MCP

#### Lista de verificación de diagnóstico

1. **Estado del servidor:** Panel de Kiro → pestaña **MCP servers** → verificará el indicador de conexión
2. **Configuración:** Verificá sintaxis JSON en `mcp.json` y que el comando y argumentos sean correctos
3. **Prerrequisitos:** Verifique las dependencias instaladas (ej. Python 3.10+ y `uv` para el servidor de AWS Docs)
4. **Registros:** Panel de salida → seleccioná **"Kiro - MCP Logs"** → buscá mensajes de error

#### Servidor de documentación de AWS

**Fallo de conexión:**
```golpecito
## Verificar instalación de uv
uv --versión

## Verificar versión de Python
Python --versión

## Probar el servidor directamente
uvx awslabs.aws-documentation-mcp-server@latest --ayuda
```

**Fallos de búsqueda/lectura:**
- Verifica tu conexión a internet
- Verifique el formato de la URL para páginas de documentación
- Probá con una consulta más sencilla

#### Servidor MCP de GitHub

**Errores de autenticación:**
- Verifica que tu token de acceso personal es válido
- Asegurate de que el token tiene los alcances requeridos (`repo`, `user`)
- Generará un nuevo token si es necesario

**Límite de tasa:**
- GitHub API tiene límites de uso: verificará el estado en los registros de MCP
- Considerá usar un token con mayor límite de tasa

---

### Obtener ayuda

Si probaste los pasos anteriores y aún necesitas ayuda:

1. 📋 Revisa las [FAQs](https://kiro.dev/faq) para preguntas comunes
2. 💬 Unite al [Discord de la comunidad](https://discord.gg/kirodotdev) para obtener ayuda
3. 🐛 Enviá un problema en [GitHub](https://github.com/kirodotdev/Kiro/issues) con:
   - Detalles del sistema operativo
   - Versión de Kiro
   - Pasos que ya intentaste
   - Mensajes de error (si aplica)

---

*📂 Capítulo: **Privacy and security > Data protection***

## Protección de datos

> **Fuente:** [kiro.dev/docs/privacy-and-security/data-protection/](https://kiro.dev/docs/privacy-and-security/data-protection/)

---

### Almacenamiento de datos

Kiro almacena tus preguntas, sus respuestas y contexto adicional (como código) para generar nuevas respuestas.

| Tipo de usuario | Dónde se almacena el contenido |
|---|---|
| **Nivel gratuito / Suscriptor individual** | Este de EE. UU. (Norte de Virginia) |
| **Usuario empresarial** | Los datos **no se almacenan** |

Con la inferencia entre regiones, el contenido puede procesarse en una región diferente dentro de la misma geografía.

---

### Cifrado de datos

#### Cifrado en tránsito
Toda la comunicación entre los clientes y Kiro, y entre Kiro y sus servicios downstream, está protegida con **TLS 1.2 o superior**.

#### Cifrado en reposo
- **Gratis / Individual:** Kiro cifra los datos usando **claves de cifrado propiedad de AWS** de AWS KMS. No es necesaria ninguna acción por parte del usuario.
- **Enterprise:** Los administradores pueden crear **claves administradas por el cliente (CMK)** de KMS para cifrar los datos. Solo se soportarán teclas simétricas. El administrador debe proporcionar la llave en la consola Kiro para activarla.

---

### Mejora del servicio

AWS puede usar cierto contenido de usuarios **Nivel gratuito** y **suscriptores individuales** para mejorar el servicio:

| Tipo de usuario | Uso para mejorar el servicio |
|---|---|
| **Gratis / Individual (inicio de sesión social / ID de constructor)** | ✅ Puede usar (prompts, código generado, respuestas) |
| **Usuario empresarial** | ❌ **No se usa** para mejorar el servicio |
| **Amazon Q Developer Pro (a través de una cuenta de AWS)** | ❌ **No se usa** para mejorar el servicio |

---

### Optar por no compartir datos

Por defecto, Kiro recopila telemetría de uso, errores, informes de fallos y contenido de usuarios Suscriptores gratuitos/individuales.

> **Usuarios empresariales:** están automáticamente excluidos de la recopilación de telemetría y contenido por AWS.

#### Optar por no participar en el IDE

1. Abrir configuración en Kiro
2. Cambiá a la sub-pestaña **Usuario**
3. Elegí **Aplicación** → **Telemetría y Contenido**
4. Para excluirte de telemetría: desmarca **Usage Analytics And Performance Metrics**
5. Para excluirte del contenido: desmarca **Recopilación de contenido para mejorar el servicio**

#### Optar por no participar en la CLI

1. Abra **Preferencias** en la aplicación Kiro CLI
2. Para telemetría: desactive el botón **Telemetría**
3. Para contenido: desactivá el interruptor **Compartir contenido de Kiro con AWS**

---

### Tipos de telemetría recopilados

- **Datos de uso:** Versión de Kiro, sistema operativo (Windows, Linux, macOS), ID de máquina anónimo
- **Métricas de rendimiento:** Recuento de solicitudes, errores y latencia para:
  - Inicio de sesión, finalización de pestañas, generación de código, dirección, hooks, generación de especificaciones, herramientas, MCP

---

*📂 Capítulo: **Privacy and security > Code references***

## Referencias de código

> **Fuente:** [kiro.dev/docs/privacy-and-security/code-references/](https://kiro.dev/docs/privacy-and-security/code-references/)

---

Las **referencias de código** son atribuciones que aparecen cuando el código generado por Kiro es similar a un código de código abierto disponible públicamente. Esto te permite revisar el origen y tomar decisiones informadas sobre su uso.

---

### Ver el registro de referencia del código

El registro de referencias de código muestra las sugerencias de código similar a código público.

1. Abra la pestaña **Output** en la barra de estado
2. Desde el menú desplegable, elija **code-references**

> ℹ️ El log solo aparece cuando code references está habilitado y Kiro generó código con referencias.

---

### Activar y desactivar referencias de códigos

Las referencias de código están **deshabilitadas por defecto**.

Para activarlas o desactivarlas:
1. Abrir **Configuración** en Kiro
2. Cambiá a la sub-pestaña **Usuario**
3. Elegí **Kiro** (o buscá "referencias de código" en la barra de búsqueda de Configuración)
4. Bajo **Code References: Reference Tracker**, marca o desmarca la opción **Permitir a Kiro generar código con referencias**

---

### Optar por no ser administrador empresarial

Los administradores Enterprise pueden deshabilitar globalmente las sugerencias de código con referencias para **todos los usuarios** del perfil.

- Los usuarios de Enterprise no tienen control sobre esta configuración — está controlado por el administrador y no puede sobreescribirse
- Se configura desde la **Consola Kiro** → Configuración

Para más información: [Configuración empresarial →](../13_Enterprise/08_Settings.md)

---

*📂 Capítulo: **Privacy and security > Compliance validation***

## Validación de cumplimiento

> **Fuente:** [kiro.dev/docs/privacy-and-security/compliance-validation/](https://kiro.dev/docs/privacy-and-security/compliance-validation/)

---

Los terceros independientes validan la seguridad y el cumplimiento normativo de los servicios en la nube de AWS, incluido Kiro.

---

### Programas de cumplimiento de AWS

Kiro está construido sobre la infraestructura de AWS, que está sujeta a una amplia gama de programas de cumplimiento. Para ver la lista completa de servicios cubiertos de AWS por programas de cumplimiento:

- [Servicios de AWS dentro del alcance del programa de cumplimiento](https://aws.amazon.com/compliance/services-in-scope/)

---

### Cumplimiento normativo

Para entender cómo validar el cumplimiento de los requisitos reglamentarios específicos al usar AWS:

- [Programas de cumplimiento de AWS](https://aws.amazon.com/compliance/programs/)
- [Compartir la responsabilidad del cumplimiento](https://docs.aws.amazon.com/whitepapers/latest/aws-risk-and-compliance/sharing-responsibility-for-compliance.html) — Documento técnico sobre riesgos y cumplimiento de AWS

---

### Recursos adicionales

| Recurso | URL |
|---|---|
| Seguridad en la nube de AWS | [aws.amazon.com/security/](https://aws.amazon.com/security/) |
| Política de IA responsable | [aws.amazon.com/ai/responsible-ai/policy/](https://aws.amazon.com/ai/responsible-ai/policy/) |
| Política de privacidad de AWS | [aws.amazon.com/privacy/](https://aws.amazon.com/privacy/) |
| Licencia Kiro | [kiro.dev/license/](https://kiro.dev/license/) |

---

*📂 Capítulo: **Privacy and security > Infrastructure security***

## Seguridad de infraestructura

> **Fuente:** [kiro.dev/docs/privacy-and-security/infrastructure-security/](https://kiro.dev/docs/privacy-and-security/infrastructure-security/)

---

Como servicio gestionado, Kiro está protegido por la **seguridad de red global de AWS**.

---

### Seguridad de la capa de transporte (TLS)

Los clientes que acceden a Kiro deben soportar:

| Requisito | Valor |
|---|---|
| **TLS mínimo** | TLS 1.2 |
| **TLS recomendado** | TLS 1.3 |
| **Suites de cifrado** | Secreto directo perfecto: DHE o ECDHE |

> ℹ️ La mayoría de los sistemas modernos (Java 7 y posteriores) soportan estos modos.

---

### Solicitar autenticación

Las solicitudes deben estar firmadas usando:
- Un **ID de clave de acceso** y **Clave de acceso secreta** asociados a un principal de IAM, o
- Credenciales de seguridad temporales generadas por **AWS Security Token Service (AWS STS)**

---

### Recursos de AWS

- [Seguridad en la nube de AWS](https://aws.amazon.com/security/)
- [Protección de infraestructura: marco de buena arquitectura de AWS] (https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/infrastructure-protection.html)

---

*📂 Capítulo: **Privacy and security > IAM permissions***

## Permisos de IAM

> **Fuente:** [kiro.dev/docs/privacy-and-security/iam-permissions/](https://kiro.dev/docs/privacy-and-security/iam-permissions/)

---

Para crear un perfil de Kiro y gestionar suscripciones, el rol que administra Kiro necesita los siguientes permisos IAM en la cuenta AWS.

---

### Permisos generales

Requeridos independientemente del almacén de identidad utilizado:

```
codewhisperer:ListProfiles
codewhisperer:CreateProfile
codewhisperer:DeleteProfile
codewhisperer:UpdateProfile
codewhisperer:TagResource
codewhisperer:UntagResource
codewhisperer:ListTagsForResource
codewhisperer:AllowVendedLogDeliveryForResource
q:ListDashboardMetrics
```

---

### Permisos de proveedores de identidad externos

Si conectas un proveedor de identidad externo (Okta, Microsoft Entra ID), también necesitarás:

```
q:ListLoginDomains
q:AssociateLoginDomain
q:DisassociateLoginDomain
q:ListScimAccessTokens
q:CreateScimAccessToken
q:DeleteScimAccessToken
q:ListGroups
q:ListUsers
q:BatchDescribeUsers
q:BatchDescribeGroups
```

---

### Recursos adicionales

| Recurso | URL |
|---|---|
| Documentación de AWS IAM | [docs.aws.amazon.com/iam/](https://docs.aws.amazon.com/iam/) |
| Mejores prácticas de IAM | [Guía de mejores prácticas de IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) |
| Protección de datos Kiro | [Protección de datos →](./01_Data%20protection.md) |
| Seguridad de infraestructura Kiro | [Seguridad de infraestructura →](./04_Infrastructure%20security.md) |
| Política de IAM empresarial (completa) | [IAM empresarial →](../13_Enterprise/10_IAM.md) |

---

*📂 Capítulo: **Privacy and security > Firewalls, proxies, and data perimeters***

## Firewalls, proxies y perímetros de datos

> **Fuente:** [kiro.dev/docs/privacy-and-security/firewalls/](https://kiro.dev/docs/privacy-and-security/firewalls/)

---

### Descripción general del tráfico de red

Kiro realiza dos tipos de conexiones salientes:

| Tipo | Descripción |
|---|---|
| **Tráfico IDE** | Solicitudes del proceso Kiro (chat, completaciones, telemetría, actualizaciones, extensiones). Respeta la configuración de proxy del IDE |
| **Tráfico del navegador** | El inicio de sesión abre el navegador por defecto. Usa la pila de red del sistema operativo y **bypasea** la configuración de proxy del IDE |

> ⚠️ Tu firewall debe permitir **ambos tipos** a nivel de red.

---

### URL principales (obligatorias)

Toda instalación de Kiro necesita las siguientes URL (inicio de sesión, chat, telemetría, actualizaciones automáticas):

| URL | Propósito |
|---|---|
| `app.kiro.dev` | Iniciar sesión y portal |
| `prod.us-east-1.auth.desktop.kiro.dev` | Autenticación |
| `prod.us-east-1.telemetry.desktop.kiro.dev` | Telemetria |
| `prod.download.desktop.kiro.dev` | Actualizaciones |
| `q.us-east-1.amazonaws.com` | Backend API (Norte de Virginia) |
| `q.eu-central-1.amazonaws.com` | API backend (Fráncfort) |

> 💡 Si tu política de red permite comodines, podrás usar `*.kiro.dev` en lugar de los primeros 4 dominios.

---

### URL del Centro de identidad de IAM

Si tu organización usa **AWS IAM Identity Center**:

```
<idc-directory-id-or-alias>.awsapps.com
oidc.<sso-region>.amazonaws.com
```

Reemplazá `idc-directory-id-or-alias` con el ID o alias de tu instancia IAM Identity Center, y `sso-region` con la región AWS donde está habilitada.

---

### Proveedores de identidad externos

Si utiliza un IdP externo (Okta o Microsoft Entra ID):

```
login.microsoftonline.com     # Microsoft Entra ID
<your-org>.okta.com           # Okta
```

Consulta con tu equipo de identidad si no estás seguro del dominio exacto.

---

### AWS GovCloud

Para **AWS GovCloud (US)**, usaremos estos puntos finales compatibles con FIPS en lugar de las URL principales:

```
q-fips.us-gov-east-1.amazonaws.com
q-fips.us-gov-west-1.amazonaws.com
```

---

### URL de gestión de suscripciones

Si usás login social (Google, GitHub, AWS Builder ID), Kiro usa **Stripe** para la facturación:

```
billing.stripe.com
checkout.stripe.com
```

> ℹ️ Los clientes Enterprise con IAM Identity Center no necesitan estos dominios.

---

### URL opcionales

Solo necesitas estas URL si usamos las características correspondientes:

| URL | Característica |
|---|---|
| `open-vsx.org` | Extensiones |
| `openvsx.eclipsecontent.org` | Extensiones |
| `github.com` | Poderes |
| `raw.githubusercontent.com` | Poderes |

---

### Configuración de proxy

Kiro respeta las variables de entorno estándar de proxy para todo el tráfico del IDE:

```
HTTP_PROXY
HTTPS_PROXY
NO_PROXY
```

También puedes configurar el proxy desde **Configuración → Proxy** dentro de Kiro.

> ⚠️ El tráfico del navegador (iniciar sesión) usa la pila de red del sistema operativo — el proxy del IDE **no aplica**. Tu firewall debe permitir las URL de IAM Identity Center y `app.kiro.dev` a nivel de rojo.

---

### Perímetros de datos

Si usas [perímetros de datos en AWS](https://aws.amazon.com/identity/data-perimeters-on-aws/), asegúrate de que tus políticas permiten a los principales de servicio de Kiro acceder a los endpoints listados en esta página.

Para controlar el nivel de VPC: [VPC Endpoints (AWS PrivateLink) →](./07_VPC%20endpoints%20(AWS%20PrivateLink).md)

---

*📂 Capítulo: **Privacy and security > VPC endpoints (AWS PrivateLink)***

## Puntos de enlace de la VPC (AWS PrivateLink)

> **Fuente:** [kiro.dev/docs/privacy-and-security/vpc-endpoints/](https://kiro.dev/docs/privacy-and-security/vpc-endpoints/)

---

AWS PrivateLink permite establecer una **conexión privada** entre tu VPC y Kiro, sin que el tráfico atraviese la Internet pública.

---

### Consideraciones

Antes de configurar un punto final de VPC para Kiro, revise las [limitaciones de puntos finales de interfaz](https://docs.aws.amazon.com/vpc/latest/privatelink/create-interface-endpoint.html#vpce-interface-limitations) en la guía de Amazon VPC.

Kiro soporta llamadas a todas sus acciones de API desde tu VPC, en el contexto de servicios configurados para trabajar con Kiro.

---

### Requisitos previos

- Cuenta AWS con permisos para crear y configurar recursos
- Una VPC ya creada en tu cuenta AWS
- Familiaridad con Amazon VPC y Kiro

---

### Creación de un punto final de interfaz VPC para Kiro

Puede crear el punto final de VPC usando la **consola de Amazon VPC** o la **AWS CLI**.

Referencia: [Creación de un punto final de interfaz →](https://docs.aws.amazon.com/vpc/latest/privatelink/create-interface-endpoint.html#create-interface-endpoint)

#### Nombres de servicios para Kiro

| Punto final | Región |
|---|---|
| `com.amazonaws.us-east-1.q` | Este de EE. UU. (Norte de Virginia) |
| `com.amazonaws.us-east-1.codewhisperer` | Este de EE. UU. (Norte de Virginia) — en solitario |
| `com.amazonaws.eu-central-1.q` | Europa (Fráncfort) |
| `com.amazonaws.us-gov-west-1.q` | AWS GovCloud (EE.UU.-Oeste) |
| `com.amazonaws.us-gov-east-1.q` | AWS GovCloud (EE.UU.-Este) |

> ℹ️ Kiro soporta perfiles de desarrolladores de Amazon Q en EE.UU. Este (N. Virginia) y Europa (Frankfurt). El punto final Amazon CodeWhisperer solo está disponible en el este de EE. UU.

#### DNS privado

Si habilita DNS privado para el endpoint, podrá hacer solicitudes a Kiro usando su nombre DNS por defecto para la región. Ejemplo:

```
q.us-east-1.amazonaws.com
```

---

### Uso de una computadora local

Para conectar a Kiro desde un equipo local a través de AWS PrivateLink:

1. **Crea una conexión VPN** entre tu dispositivo local y tu VPC
   - [Guía del usuario del cliente VPN de AWS →](https://docs.aws.amazon.com/vpn/latest/clientvpn-user/client-vpn-user-what-is.html)

2. **Crear el punto final de la VPC de interfaz** para Kiro
   - [Instrucciones arriba ↑](#creando-una-interfaz-vpc-endpoint-para-kiro)

3. **Configurar un punto final entrante de Amazon Route 53**
   - Esto permite usar el nombre DNS del endpoint de Kiro desde tu dispositivo local
   - [Enrutamiento a un punto final de interfaz VPC →](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-to-vpc-interface-endpoint.html)