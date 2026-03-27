# Migrating from VS Code

> **Source:** [kiro.dev/docs/guides/migrating-from-vscode/](https://kiro.dev/docs/guides/migrating-from-vscode/)

---

La base de VS Code de Kiro permite compatibilidad completa con tu entorno de desarrollo. Podés transferir tu configuración personalizada — extensiones, temas, settings y shortcuts — sin problemas de compatibilidad.

---

## Profile Migration

### Exporting a Profile from VS Code

1. Abrí el Command Palette en VS Code (`Cmd/Ctrl + Shift + P`)
2. Escribí y seleccioná **"Preferences: Open Profiles (UI)"**
3. Localizá el perfil deseado en el sidebar
4. Accedé al menú de 3 puntos y elegí **Export**
5. Guardá localmente o publicá en un GitHub Gist

### Importing a Profile to Kiro

1. Abrí el Command Palette de Kiro (`Cmd/Ctrl + Shift + P`)
2. Escribí y seleccioná **"Preferences: Open Profiles (UI)"**
3. Abrí el dropdown junto a **New Profile** y seleccioná **Import Profile**
4. Pegá la URL del GitHub Gist o buscá tu archivo de export local
5. Confirmá con **Import** para guardar la configuración
6. Activá tu perfil seleccionándolo en el sidebar y haciendo click en el checkmark ✓

**Tu perfil importado incluye:**
- Temas de color y preferencias de UI
- Settings del editor y workspace
- Atajos de teclado y keybindings personalizados

---

## Settings and Interface

### Settings Menus

Kiro extiende la arquitectura de settings de VS Code con controles dedicados para capacidades de IA:

**Kiro Settings:**
- `Cmd/Ctrl + Shift + P` → "Preferences: Open Settings (UI)"
- Navegá a la sección **Kiro Agent**
- Gestioná comportamientos de IA, automatización del agente, trusted commands y features exclusivos de Kiro

**VS Code Settings:**
- Mismo acceso: `Cmd/Ctrl + Shift + P` → "Preferences: Open Settings (UI)"
- Tus preferencias estándar de VS Code siguen funcionando junto a los settings de Kiro

### Version Updates

Kiro se mantiene sincronizado con el ciclo de desarrollo de VS Code mediante rebasing regular. Se incorporan las últimas features seleccionando releases estables de VS Code para asegurar confiabilidad junto a las mejoras de IA.

---

## Extension Compatibility

Kiro usa el **registro de extensiones OpenVSX**, asegurando compatibilidad con extensiones open-source.

| Tipo de extensión | Compatibilidad |
|---|---|
| **Language extensions** | Funcionalidad completa para extensiones disponibles en OpenVSX |
| **Theme extensions** | Compatibilidad visual completa con temas de OpenVSX |
| **Debugging extensions** | Workflows de debugging sin interrupciones para extensiones compatibles |
| **Git extensions** | Aumentadas con generación inteligente de commits y code review automatizado |

> ⚠️ Solo las extensiones disponibles en el **registro OpenVSX** pueden importarse. Algunas extensiones exclusivas del VS Code Marketplace pueden no estar disponibles en Kiro.

---

## Quick Checklist

- [ ] Exportar perfil de VS Code (extensiones, settings, keybindings)
- [ ] Importar perfil en Kiro
- [ ] Verificar que las extensiones críticas estén disponibles en OpenVSX
- [ ] Revisar los settings de **Kiro Agent** para configurar el comportamiento de IA
- [ ] Probar el flujo de trabajo habitual para confirmar compatibilidad