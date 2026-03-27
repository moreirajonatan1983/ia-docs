# Integración de terminales

> **Fuente:** [kiro.dev/docs/chat/terminal/](https://kiro.dev/docs/chat/terminal/)

---

En lugar de memorizar sintaxis de comandos o cambiar entre ventanas, describe lo que quieres hacer y Kiro traduce tus solicitudes en comandos ejecutables, mantiene el contexto entre operaciones y proporciona un sistema de aprobación seguro.

---

## Empezando

Simplemente describí lo que querés hacer en lenguaje natural:

- "Instalar las dependencias del proyecto"
- "Verificar el estado de git"
- "Buscar todos los archivos TypeScript en la carpeta src"
- "Ejecutar el servidor de desarrollo"

Kiro traduce tu solicitud al comando apropiado y pide aprobación antes de ejecutar.

---

## Cómo funciona

Cuando Kiro sugiere un comando, tenés cuatro opciones:

| Opción | Acción |
|---|---|
| **Modificar** | Editar el comando antes de ejecutar |
| **Rechazar** | Cancelar la ejecución |
| **Ejecutar** | Ejecutar una vez |
| **Corre y confía** | Ejecutar y confiar en comandos similares en el futuro |

Los comandos de larga ejecución (como servidores de desarrollo) son gestionados automáticamente por Kiro en terminales dedicadas sin bloquear tu flujo de trabajo.

---

## Aprobación y seguridad de comandos

### Comandos de confianza

Configurará qué confiar comandos automáticamente en:
**Configuración → Kiro Agent: Comandos confiables**

Disponible a nivel usuario (global) y a nivel Workspace.

#### Coincidencia exacta
```json
["instalación npm", "estado de git"]
```
- ✅ `npm install` → aprobado automáticamente
- ✅ `git status` → aprobado automáticamente
- ❌ `npm install --save` → requiere aprobación (solo coincidencia exacta)

#### Coincidencia parcial de comodines
```json
["instalación npm *"]
```
- ✅ `npm install` → aprobado
- ✅ `npm install --save` → aprobado
- ✅ `npm install express` → aprobado
- ❌ `npm run build` → requiere aprobación

#### Coincidencia completa de comodines
```json
["npm *", "git *"]
```
- ✅ Todos los comandos `npm` y `git` → auto-aprobado
- ❌ `docker build.` → requiere aprobación

#### Confianza universal
```json
["*"]
```
> ⚠️ **Extremadamente peligroso.** Solo usá esto si controlás completamente el ambiente.

### Lista de denegaciones de comandos

La lista de denegación impide la aprobación automática de comandos con patrones específicos, independientemente de los Settings de confianza. Estados Unidos **coincidencia de subcadenas**.

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

> La lista de denegados **se revisa antes** que los Settings de confianza. Incluso con `["*"]` entrust, los comandos denegados requieren aprobación manual.

---

## Usando el contexto del terminal

Referencia la salida reciente de tu terminal con `#terminal`:

```
#terminal analyze the error from the last npm run build
```

> ⚠️ `#terminal` siempre hace referencia a la terminal activa/visible. Si tiene múltiples terminales abiertos, asegúrese de que la correcta esté activada antes de usar `#terminal`.

**Capacidad:**
- Análisis de errores — Entender por qué fallaron los comandos
- Interpretación de salida — Explicar resultados complejos y logs
- Acciones de seguimiento — Sugerir próximos pasos basados en resultados reales
- Reconocimiento de patrones — Identificar problemas recurrentes
- Debug del entorno — Resolver conflictos de sistema y dependencias