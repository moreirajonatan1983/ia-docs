# Modelos

> **Fuente:** [kiro.dev/docs/models/](https://kiro.dev/docs/models/)

---

Kiro admite múltiples modelos de IA. Puede cambiar de modelo desde el menú desplegable de la interfaz de chat; su selección se aplica a todos los mensajes posteriores de la conversación.

---

## Comparación rápida

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

## Detalles del modelo

### Automático *(recomendado)*

El enrutador modelo de Kiro. Auto combina múltiples modelos de frontera con técnicas de optimización para ofrecer la mejor relación calidad-costo. Elige automáticamente el modelo óptimo para cada tarea y ofrece resultados de clase Sonnet 4. Auto utiliza los mejores modelos LLM de su clase (Claude Sonnet 4 y similares) y mantiene un nivel de alta calidad para garantizar que los resultados se comparen o superen los modelos individuales disponibles para usted.

---

### Claude Opus 4.6

El modelo más capaz de Anthropic con codificación de última generación y rendimiento agente. Puntuaciones máximas en Terminal-Bench 2.0 y SWE-bench Verified para codificación agente. Se mantiene productivo durante sesiones más largas sin cambios de contexto y maneja bases de código de varios millones de líneas, planificando por adelantado y adaptándose según sea necesario. Las capacidades mejoradas de depuración y revisión de código le permiten detectar sus propios errores y pensar con más cuidado en problemas complejos, revisando el razonamiento antes de comprometerse. [Más información →](https://www.anthropic.com/research/claude-opus-4-6)

---

### Claude Opus 4.5

El modelo más inteligente de Anthropic, que combina la máxima capacidad con un rendimiento práctico. Mejoras significativas en razonamiento, codificación y resolución de problemas a un precio más accesible que los modelos Opus anteriores. Maneja bien las compensaciones y la ambigüedad en múltiples sistemas, lo que lo hace adecuado para los desafíos de desarrollo de software más sofisticados. [Más información →](https://www.anthropic.com/news/claude-opus-4-5)

---

### Claude Soneto 4.6

Una actualización completa de Sonnet 4.5 que se acerca a la inteligencia de Opus 4.6 y al mismo tiempo es más eficiente en términos de token. Destaca en flujos de trabajo de desarrollo iterativos y mantiene el contexto durante sesiones largas. Maneja funciones de agente principal y subagente en procesos multimodelo, lo que lo hace ideal para equipos que utilizan Powers de Kiro y subagentes personalizados. [Más información →](https://www.anthropic.com/news/claude-sonnet-4-6)

---

### Claude Soneto 4.5

El mejor modelo de Anthropic para codificación y agentes complejos, con la mayor inteligencia en la mayoría de las tareas. Lo último en tecnología SWE-bench Verificado con operación autónoma extendida durante horas con uso efectivo de herramientas. Mejora de la planificación, el diseño de sistemas y la ingeniería de seguridad. [Más información →](https://www.anthropic.com/news/claude-sonnet-4-5)

---

### Claude Soneto 4.0

Acceso directo a Claude Sonnet 4.0 de Anthropic para usuarios que prefieren una selección de modelos consistente. Mismo modelo para todas las interacciones sin capas de enrutamiento ni optimización. Control total y transparencia total, con comportamiento predecible para flujos de trabajo que dependen de características específicas del modelo. [Más información →](https://www.anthropic.com/news/claude-4)

---

### Claude Haiku 4.5

El modelo más rápido de Anthropic con un rendimiento cercano a la frontera. Iguala el rendimiento de Sonnet 4 en razonamiento y codificación a más del doble de velocidad. Inteligencia cercana a la frontera a un costo de un tercio y el primer modelo Haiku con capacidades de pensamiento ampliadas. [Más información →](https://www.anthropic.com/news/claude-haiku-4-5)

---

### MiniMax M2.5

Modelo de peso abierto que iguala el rendimiento de codificación de primera clase a una fracción del costo. Capacitado con aprendizaje reforzado en cientos de miles de entornos del mundo real, brindando resultados sólidos en todo el ciclo de vida de desarrollo, desde el diseño del sistema hasta la revisión del código. **Multiplicador de crédito de 0,25x** con inferencia ejecutándose en el este de EE. UU. (Norte de Virginia). [Más información →](https://www.minimax.io/news/minimax-m25)

---

### Búsqueda profunda 3.2

Modelo de peso abierto más adecuado para flujos de trabajo agentes y generación de código. Maneja bien largas cadenas de llamadas de herramientas, sesiones con estado y razonamiento de varios pasos. **Multiplicador de crédito de 0,25x** con inferencia ejecutándose en el este de EE. UU. (Norte de Virginia). [Más información →](https://api-docs.deepseek.com/news/news250325)

---

### MiniMax M2.1

Modelo de peso abierto más adecuado para programación multilingüe y generación de UI. Ofrece resultados sólidos en Rust, Go, C++, Kotlin, TypeScript y otros. **Multiplicador de crédito de 0,15 veces** con inferencia en el este de EE. UU. (Norte de Virginia) y la UE (Frankfurt). [Más información →](https://minimax.io/news/minimax-m21)

---

## Cómo los modelos se comportan de manera diferente

No todos los modelos funcionan de la misma manera. Comprender estas diferencias le ayudará a elegir la correcta:

| Dimensión | Obra | Soneto | haikus |
|---|---|---|---|
| **Profundidad de planificación** | Piensa más, considera casos extremos, revisa el razonamiento | Más directo, empieza a funcionar antes | Planificación inicial más rápida y mínima |
| **Autocorrección** | Opus 4.6 detecta sus propios errores durante su revisión | Estándar | Estándar |
| **Resistencia de la sesión** | Mantiene el enfoque durante largas sesiones de varios archivos | Bueno para sesiones medias | Lo mejor para interacciones breves y enfocadas |
| **Nivel de iniciativa** | Toma más iniciativa, cambios más amplios | Conservador, se atiene a lo pedido | Conservador |

---

## Ciclo de vida del modelo

Los modelos en Kiro pasan por dos etapas. Cada etapa refleja la madurez del modelo y el nivel de soporte que puede esperar.

> **Nota:** Las solicitudes de inferencia para **modelos experimentales** se pueden procesar en varias regiones de AWS a nivel mundial para optimizar la disponibilidad y el rendimiento. Consulte [protección de datos](https://kiro.dev/docs/privacy-and-security/data-protection/#global-cross-region-inference-for-experimental-features) para obtener detalles sobre la inferencia entre regiones.

---

## Mejores prácticas

- **Comience con Auto** para la mayoría del trabajo. Optimiza tanto la calidad como el coste de forma automática.
- **Cambie a Opus** cuando se encuentre con un problema complejo o necesite un trabajo continuo con varios archivos.
- **Utilice Haiku** para iteraciones rápidas, correcciones simples o cuando desee conservar créditos.
- **Supervise su uso** en la [configuración de su cuenta](https://kiro.dev/docs/billing/) para comprender cómo la elección del modelo afecta el consumo.
- **Incluye el costo del modelo en tu nivel:** Si usas principalmente Opus, considera Pro+ o Power para obtener más créditos. Consulte [planes y facturación](https://kiro.dev/docs/billing/) para obtener más detalles.