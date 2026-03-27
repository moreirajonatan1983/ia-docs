# Diagnostics Tool

> **Source:** [kiro.dev/docs/chat/diagnostics/](https://kiro.dev/docs/chat/diagnostics/)

---

La herramienta de diagnósticos de Kiro ayuda al agente a entender y trabajar con tu código integrándose con las extensiones del IDE. Proporciona detección de errores en tiempo real, validación de sintaxis y análisis de código que mejora la calidad de la asistencia AI.

---

## Overview

La integración con extensiones del IDE provee:

- **Real-time error detection** — Errores de sintaxis, type mismatches y problemas de compilación
- **Language-specific insights** — Semántica del lenguaje, imports y dependencias
- **Code quality analysis** — Reglas de linting, violaciones de estilo y best practices
- **Contextual awareness** — Estructura del proyecto, APIs disponibles y definiciones de tipos

---

## How It Works

La herramienta de diagnósticos se integra con las extensiones de lenguaje instaladas. Cuando tenés extensiones de lenguaje instaladas, Kiro accede a la información diagnóstica del language server para entender mejor tu código.

La herramienta funciona **automáticamente durante la ejecución del agente** — sin configuración adicional necesaria.

---

## Getting Started

1. **Instalar extensiones de lenguaje** para tus lenguajes de programación:
   - [Python Guide →](https://kiro.dev/docs/guides/languages-and-frameworks/python-guide/#extensions)
   - [TypeScript/JavaScript Guide →](https://kiro.dev/docs/guides/languages-and-frameworks/typescript-javascript-guide/#suggested-extensions)
   - [Java Guide →](https://kiro.dev/docs/guides/languages-and-frameworks/java-guide/#suggested-extensions)

2. **Abrir un archivo** en tu lenguaje objetivo para activar el language server

La herramienta funciona automáticamente a partir de ese punto.

---

## Troubleshooting

Si el agente no detecta problemas de código:

- **Extensión no detectada:** Verificar que la extensión está habilitada en el panel de Extensiones
- **Language server inactivo:** Output Panel → buscar mensajes de error de language servers
- **Server no inicia:** Command Palette → "Reload Window"
- **Capacidades desactualizadas:** Mantener extensiones actualizadas

---

## Next Steps

- [Language guides →](https://kiro.dev/docs/guides/languages-and-frameworks) para setup por lenguaje
- [Combining diagnostics with dev servers →](https://kiro.dev/docs/chat/dev-servers/#combining-with-code-diagnostics) para un workflow completo