# Herramienta de diagnóstico

> **Fuente:** [kiro.dev/docs/chat/diagnostics/](https://kiro.dev/docs/chat/diagnostics/)

---

La herramienta de diagnóstico de Kiro ayuda al agente a entender y trabajar con tu código integrándose con las extensiones del IDE. Proporciona detección de errores en tiempo real, validación de sintaxis y análisis de código que mejora la calidad de la asistencia AI.

---

## Descripción general

La integración con extensiones del IDE proporciona:

- **Detección de errores en tiempo real** — Errores de sintaxis, discrepancias de tipos y problemas de compilación
- **Información específica del idioma** — Semántica del lenguaje, importaciones y dependencias
- **Análisis de calidad de código** — Reglas de linting, violaciones de estilo y mejores prácticas
- **Conciencia contextual** — Estructura del proyecto, APIs disponibles y definiciones de tipos

---

## Cómo funciona

La herramienta de diagnóstico se integra con las extensiones de lenguaje instaladas. Cuando tenga extensiones de lenguaje instaladas, Kiro accede a la información diagnóstica del servidor de lenguaje para entender mejor su código.

La herramienta funciona **automáticamente durante la ejecución del agente** — sin configuración adicional necesaria.

---

## Empezando

1. **Instalar extensiones de lenguaje** para tus lenguajes de programación:
   - [Guía de Python →](https://kiro.dev/docs/guides/languages-and-frameworks/python-guide/#extensions)
   - [Guía de TypeScript/JavaScript →](https://kiro.dev/docs/guides/languages-and-frameworks/typescript-javascript-guide/#suggested-extensions)
   - [Guía de Java →](https://kiro.dev/docs/guides/languages-and-frameworks/java-guide/#suggested-extensions)

2. **Abrir un archivo** en tu lenguaje objetivo para activar el servidor de idiomas

La herramienta funciona automáticamente a partir de ese punto.

---

## Solución de problemas

Si el agente no detecta problemas de código:

| Problema | Solución |
|---|---|
| Extensión no detectada | Verificar que la extensión está habilitada en el panel de Extensiones |
| Servidor de idiomas inactivo | Panel de salida → buscar mensajes de error de servidores de idiomas |
| Servidor no iniciado | Paleta de comandos → "Recargar ventana" |
| Capacidades desactualizadas | Mantener extensiones actualizadas |

---

## Próximos pasos

- [Guías de idiomas →](https://kiro.dev/docs/guides/languages-and-frameworks) para configuración por idioma
- [Combinación de diagnósticos con servidores de desarrollo →](https://kiro.dev/docs/chat/dev-servers/#combining-with-code-diagnostics) para un flujo de trabajo completo