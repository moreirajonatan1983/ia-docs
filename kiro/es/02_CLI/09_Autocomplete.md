# Finalizaciones y Autocompletar

> **Fuente:** [kiro.dev/docs/cli/autocomplete/](https://kiro.dev/docs/cli/autocomplete/)

---

Kiro CLI proporciona sugerencias y completaciones de comandos impulsadas por IA para cientos de herramientas CLI populares, lo que hace que la línea de comandos funcione más rápido y con mayor precisión.

---

## Menú desplegable de autocompletar

El menú desplegable de autocompletar aparece a la **derecha del cursor** al escribir comandos y muestra las opciones, subcomandos y argumentos disponibles que puede seleccionar usando las teclas de flecha.

### Usando Autocompletar

- Comience a escribir un comando
- El menú desplegable aparece automáticamente con sugerencias.
- Utilice **teclas de flecha** para navegar
- Presione **Tab** o **Enter** para aceptar una sugerencia.

### Configuración

El comportamiento de autocompletar se puede configurar en la configuración de Kiro CLI. Consulte la [referencia de configuración de CLI](https://kiro.dev/docs/cli/reference/) para conocer las opciones disponibles.

---

## Sugerencias en línea

Las sugerencias en línea aparecen como **"texto fantasma"** gris directamente en la línea de comando a medida que escribe. Esta función funciona independientemente del menú desplegable.

### Uso de sugerencias en línea

- Escriba el comienzo de un comando
- Aparece un texto fantasma que muestra la finalización prevista.
- Presione **Tab** para aceptar la sugerencia completa
- Presione **→** (flecha derecha) para aceptar palabra por palabra
- Continúe escribiendo para descartar y anular la sugerencia.

### Gestión de sugerencias en línea

Active o desactive las sugerencias en línea en la configuración de su shell o en la configuración de CLI.

---

## Herramientas compatibles

Kiro CLI proporciona complementos para cientos de herramientas populares, entre las que se incluyen:

**Herramientas populares:** `git`, `docker`, `kubectl`, `npm`, `yarn`, `pip`, `cargo`, `make`, `terraform`, `aws`

**Herramientas de lenguaje:** `node`, `python`, `go`, `ruby`, `java`, `rustc`, `gcc`, `mvn`, `gradle`

**Herramientas del sistema:** `ls`, `cd`, `grep`, `find`, `curl`, `ssh`, `chmod`, `systemctl`

---

## Solución de problemas

### Autocompletar no funciona

- Verifique que Kiro CLI esté instalado correctamente y en su RUTA
- Reinicia tu terminal después de la instalación
- Verifique que la integración de shell esté habilitada en su perfil (`.bashrc`, `.zshrc`, etc.)

### Problemas de sugerencias en línea

- Asegúrese de que su emulador de terminal admita las secuencias de escape requeridas
- Verifique que las sugerencias en línea estén habilitadas en su configuración Kiro CLI