# Modelos

> **Fuente:** [kiro.dev/docs/models/](https://kiro.dev/docs/models/)

---

Kiro admite múltiples modelos de IA. Podés cambiar el modelo utilizando el menú desplegable en la interfaz del chat; tu selección se aplicará a todos los mensajes posteriores dentro de esa conversación.

---

## Comparación rápida

El costo es relativo al modelo **Auto (valor de referencia de 1.0x)**. Por ejemplo, una tarea consumirá 10 créditos en Auto, pero costaría unos 22 créditos en Opus, 4 créditos en Haiku, o 0.5 créditos en Qwen3 Coder Next.

| Modelo | Mejor para | Multiplicador de costos |
|---|---|---|
| **Auto** *(recomendado)* | Uso general, mejor relación calidad/coste | 1.0x |
| **Claude Opus 4.6** | Programación agente compleja, depuración, bases de código gigantes | ~2.2x |
| **Claude Opus 4.5** | Razonamiento avanzado, desafíos sofisticados | ~2.2x |
| **Claude Sonnet 4.6** | Flujos de iteración rápida, pipelines multimodelo | ~1.0x |
| **Claude Sonnet 4.5** | Agentes complejos, uso autónomo extendido | ~1.0x |
| **Claude Sonnet 4.0** | Selección de modelo predecible y consistente | ~1.0x |
| **Claude Haiku 4.5** | Iteraciones súper rápidas, arreglos menores, ahorro de créditos | ~0.4x |
| **MiniMax M2.5** | Ciclo de vida completo del desarrollo, revisión de código | 0.25x |
| **DeepSeek 3.2** | Flujos de trabajo agentes, generación de código | 0.25x |
| **MiniMax M2.1** | Programación multilingüe, generación de UI | 0.15x |
| **Qwen3 Coder Next** | Tareas rápidas de código | 0.5x |

---

## Detalles del modelo

### Auto *(recomendado)*

Es el enrutador de modelos (model router) propio de Kiro. Combina múltiples modelos de frontera con técnicas de optimización bajo la manga para ofrecer la mejor relación precio-calidad. Elige automáticamente el modelo óptimo para cada tarea particular garantizando resultados del calibre de Sonnet 4. Utiliza los mejores modelos LLM de su clase para mantener la vara altísima.

### Claude Opus 4.6

Es el modelo más capaz de Anthropic en temas de programación agente de vanguardia. Obtiene puntajes máximos en benchmarks como Terminal-Bench 2.0 y SWE-bench Verified. Se mantiene totalmente productivo y enfocado durante sesiones larguísimas sin perder contexto, logrando manejar bases de código millonarias, planificando la arquitectura y adaptándose según vayas pidiendo. Posee capacidades superiores de depuración que lo ayudan a atrapar sus propios bugs y a pensar cuidadosamente en problemas muy complejos. [Más información →](https://www.anthropic.com/research/claude-opus-4-6)

### Claude Opus 4.5

El modelo más "inteligente" de Anthropic, logrando un balance de máxima capacidad con rendimiento práctico y siendo súper certero con desafíos complejos, por un precio algo más accesible que sus predecesores de la familia Opus. [Más información →](https://www.anthropic.com/news/claude-opus-4-5)

### Claude Sonnet 4.6

Una evolución enorme desde Sonnet 4.5 que literalmente roza la inteligencia de un Opus 4.6, pero muchísimo más eficiente a nivel de tokens. Brilla en flujos interativos de desarrollo donde se requiere que maneje el contexto vivo de sesiones largas. Un campeón actuando tanto de "Agente líder" como delegando a Subagentes en ciclos multimodelo, lo que lo hace ideal si usás sus configuraciones avanzadas. [Más información →](https://www.anthropic.com/news/claude-sonnet-4-6)

### Claude Sonnet 4.5

Para muchísima gente, el mejor de Anthropic enfocado a la programación directa y la ejecución de herramientas lógicas (tool calling). Soporta operar autónomamente durante horas seguidas manejando el contexto para la planificación estricta y mejorando su ingeniería de seguridad. [Más información →](https://www.anthropic.com/news/claude-sonnet-4-5)

### Claude Sonnet 4.0

Una vía directa (sin filtros ni optimizadores por encima) hacia Claude Sonnet 4.0, ideal para cuando tu flujo de trabajo de CI/CD o testing depende exclusivamente del comportamiento exacto, cerrado y transparente de esta versión particular y necesitás cero factores mágicos encendidos. [Más información →](https://www.anthropic.com/news/claude-4)

### Claude Haiku 4.5

El rey de la velocidad de Anthropic con capacidades que raspan el nivel de frontera. Iguala en lógica y código al mismísimo Sonnet 4, ¡solamente que viaja al doble de velocidad! Brinda una inteligencia brutal de última generación por solo un tercio del costo habitual. [Más información →](https://www.anthropic.com/news/claude-haiku-4-5)

### MiniMax M2.5

Modelo *open weight* que iguala en rendimiento al entorno cerrado actual, pero consumiendo poquísimo. Fue entrenado con *Reinforcement Learning* en cientos de miles de contextos, devolviendo código sólido de diseño y revisión. Tiene un multiplicador hiper-bajo de **0.25x** procesando desde el Este de EEUU. [Más información →](https://www.minimax.io/news/minimax-m25)

### DeepSeek 3.2

Modelo *open weight* enfocado magistralmente a ser el rey de los flujos agentes automatizados y la generación de código. Puede manejar cadenas largas de ejecución de herramientas (*tool-calling*) y razonamiento matemático o lógico. Trabaja bajo el multiplicador de **0.25x**. [Más información →](https://api-docs.deepseek.com/news/news250325)

### MiniMax M2.1

La versión más orientada a la generación rápida de interfaces de usuario (UI) y programación puramente multilenguaje con resultados tremendamente fiables en Rust, Go, C++, Kotlin y TypeScript. Imbatible en precio con un multiplicador de **0.15x**. [Más información →](https://minimax.io/news/minimax-m21)

---

## Cómo se comportan de forma diferente (Comportamientos)

No todos los modelos "piensan" ni encaran los temas igual. Entender cómo es cada uno por debajo te asegura elegir la mejor herramienta:

- **Profundidad de planificación:** Los modelos Opus toman una pausa para planificar enfoques de múltiples pasos, considerar *edge-cases*, y revisar de arriba a abajo su lógica algorítmica. Sonnet y Haiku van directo al grano: se zambullen a programar al instante e iteran más rápido.
- **Autocorrección:** Opus 4.6 en particular es infinitamente superior dándose cuenta de un error estúpido propio en plena ejecución y auto-arreglándolo o depurándolo. Si le pedís código y te vienen un par de bugs, cambiar a Opus por un rato hace magia.
- **Resistencia de la sesión:** Para tareas larguísimas (como implementar y seguir al pie de la letra un archivo de Spec con 40 pasos), Opus se mantiene inquebrantable a medida que el prompt crece monstruosamente. Haiku y Sonnet son muy ágiles siempre y cuando vayas trabajando en interacciones un poco más atómicas (aisladas).
- **Nivel de iniciativa:** Opus suele tomar iniciativa arriesgada y mandarse a reescribir funciones si encuentra que "es por un bien mayor" arquitectónico. Sonnet suele ser mucho más conservador limitándose exclusivamente a hacer "solamente lo que el usuario le pide". 

---

## Ciclo de vida de los modelos

Kiro procesa los modelos en dos estados. Cada estado es un espejo de qué tan sólido y testeado está el modelo dentro del mundo del código real.

> **Nota:** Por obvias razones, al elegir **modelos experimentales** (esos modelos exóticos que recién salen al mercado), Kiro se reserva el derecho de routear las inferencias en decenas de regiones mundiales de AWS tratando de esquivar cuellos de botella para traerte las cosas rápido. Leé la guía de [Protección de datos](https://kiro.dev/docs/privacy-and-security/data-protection) si querés entender exactamente en qué lugares del mundo "piensan" los modelos.

---

## Mejores prácticas

- **Arrancá usando Auto** para el 90% de tus tareas diarias. Automáticamente encuentra un equilibrio sublime entre cuánto pagás y cuán bien tira código.
- **Pegá el salto a Opus** ni bien te comiences a chocar con una pared (bloqueador matemático) en un problema complejo o necesites que el agente edite 5 archivos a la vez manteniendo la sintonía.
- **Acordate de Haiku** si necesitás iteraciones veloces que vayan a los bifes o estés acortando costos drásticamente.
- **Revisá seguido tus consumos** dentro de tu [Configuración de la cuenta](https://kiro.dev/docs/billing/) para no asustarte con el multiplicador.
- Considerá los planes **Pro+ o Power** si en tu empresa respiran el aire de Opus noche y día, así evitan quedarse cortos. Toda la info [acá](https://kiro.dev/docs/billing/).