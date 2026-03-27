# Migrar desde VS Code

> **Fuente:** [kiro.dev/docs/guides/migrating-from-vscode/](https://kiro.dev/docs/guides/migrating-from-vscode/)

---

La base de VS Code de Kiro permite compatibilidad completa con tu entorno de desarrollo. Podés transferir tu configuración personalizada (extensiones, temas, configuraciones y accesos directos) sin problemas de compatibilidad.

---

## Migración de perfil

### Exportación de un perfil desde VS Code

1. Abra la paleta de comandos en VS Code (`Cmd/Ctrl + Shift + P`)
2. Escribí y seleccioná **"Preferencias: Abrir perfiles (UI)"**
3. Localice el perfil deseado en la barra lateral
4. Accedé al menú de 3 puntos y elige **Exportar**
5. Guarda localmente o publica en un GitHub Gist

### Importando un perfil a Kiro

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

## Configuración e interfaz

### Menús de configuración

Kiro amplía la arquitectura de configuración de VS Code con controles dedicados para capacidades de IA:

**Configuración de Kiro:**
- `Cmd/Ctrl + Shift + P` → "Preferencias: Abrir Configuración (UI)"
- Navegá a la sección **Kiro Agent**
- Gestioná comportamientos de IA, automatización del agente, comandos confiables y características exclusivas de Kiro

**Configuración del código VS:**
- Mismo acceso: `Cmd/Ctrl + Shift + P` → "Preferencias: Abrir Configuración (UI)"
- Tus preferencias estándar de VS Code siguen funcionando junto a las configuraciones de Kiro

### Actualizaciones de versión

Kiro se mantiene sincronizado con el ciclo de desarrollo de VS Code mediante rebase regular. Se incorporan las últimas características seleccionando versiones estables de VS Code para asegurar confiabilidad junto a las mejoras de IA.

---

## Compatibilidad de extensiones

Kiro usa el **registro de extensiones OpenVSX**, asegurando compatibilidad con extensiones de código abierto.

| Tipo de extensión | Compatibilidad |
|---|---|
| **Extensiones de idiomas** | Funcionalidad completa para extensiones disponibles en OpenVSX |
| **Extensiones de tema** | Compatibilidad visual completa con temas de OpenVSX |
| **Extensiones de depuración** | Flujos de trabajo de depuración sin interrupciones para extensiones compatibles |
| **Extensiones de Git** | Aumentadas con generación inteligente de commits y revisión de código automatizada |

> ⚠️ Solo las extensiones disponibles en el **registro OpenVSX** pueden importarse. Algunas extensiones exclusivas del VS Code Marketplace pueden no estar disponibles en Kiro.

---

## Lista de verificación rápida

- [] Exportar perfil de VS Code (extensiones, configuraciones, combinaciones de teclas)
- [] Importar perfil en Kiro
- [] Verificar que las extensiones críticas estén disponibles en OpenVSX
- [] Revisar los ajustes de **Kiro Agent** para configurar el comportamiento de IA
- [ ] Probar el flujo de trabajo habitual para confirmar compatibilidad