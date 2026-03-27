# Guías

> **Fuente:** [kiro.dev/docs/guides/](https://kiro.dev/docs/guides/)

---

Guías oficiales paso a paso para aprender Kiro a través de escenarios prácticos.

---

## Guías disponibles

| Guía | Descripción |
|---|---|
| [Aprende jugando →](https://kiro.dev/docs/guides/learn-by-playing/) | Cree un proyecto de juego real mientras aprende las potentes funciones de Kiro a través de tutoriales interactivos prácticos |
| [Soporte de idiomas →](https://kiro.dev/docs/guides/languages-and-frameworks/) | Guías específicas del marco para React, Python, Go y más para ayudarlo a aprovechar Kiro al máximo con su pila tecnológica |
| [Migración desde VS Code →](https://kiro.dev/docs/guides/migrate-from-vscode/) | Realice una transición perfecta de VS Code a Kiro con una migración con un solo clic que incluye todas sus extensiones y configuraciones |

---

## Migrar desde VS Code

La base VS Code de Kiro permite una compatibilidad total con su entorno de desarrollo. Puede transferir su configuración personalizada (extensiones, temas, configuraciones y accesos directos) sin problemas de compatibilidad.

### Migración de perfil

1. Abra la paleta de comandos: `Cmd+Shift+P` (Mac) / `Ctrl+Shift+P` (Windows/Linux)
2. Busque **"Importar perfil desde VS Code"**
3. Kiro detectará e importará automáticamente sus perfiles de VS Code

#### Migración manual de perfiles

Si la migración automática no funciona:
1. En VS Code: `Cmd+Shift+P` → "Perfiles: Exportar perfil" → guardar como `.code-profile`
2. En Kiro: `Cmd+Shift+P` → "Perfiles: Importar perfil" → seleccione el archivo

### Configuración e interfaz

| Artículo | Cómo acceder |
|---|---|
| **Configuración de Kiro** | `Cmd/Ctrl+Shift+P` → "Preferencias: Abrir Configuración (UI)" → navegue a la sección Kiro Agent |
| **Configuración del código VS** | Misma ruta de la paleta de comandos: sus preferencias de VS Code existentes siguen siendo completamente funcionales |

Kiro amplía la arquitectura de configuración de VS Code con controles dedicados para:
- Comportamientos de IA y automatización de agentes.
- Comandos confiables
- Funciones exclusivas de Kiro (dirección, especificaciones, hooks)

### Actualizaciones de versión

Kiro se mantiene sincronizado con el ciclo de desarrollo de VS Code mediante cambios de base regulares. Incorporamos las funciones más recientes y seleccionamos versiones estables de VS Code para garantizar la confiabilidad junto con mejoras de IA.

### Compatibilidad de extensiones

Kiro utiliza el **registro de extensión OpenVSX**. Las extensiones disponibles en OpenVSX migran sin problemas:

| Tipo de extensión | Compatibilidad |
|---|---|
| Extensiones de idiomas | Funcionalidad completa para extensiones disponibles en OpenVSX |
| Extensiones de temas | Compatibilidad visual completa |
| Extensiones de depuración | Flujos de trabajo de depuración ininterrumpidos para extensiones compatibles |
| Extensiones de Git | Ampliado con generación de commit inteligente y revisión de código automatizada |

> ⚠️ Solo se pueden importar extensiones disponibles en el **registro OpenVSX**. Es posible que algunas exclusivas de VS Code Marketplace no estén disponibles en Kiro.