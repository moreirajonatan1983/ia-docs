# Protocolo de cliente agente (ACP)

> **Fuente:** [kiro.dev/docs/cli/acp/](https://kiro.dev/docs/cli/acp/)

---

ACP (Agent Client Protocol) es un protocolo estandarizado para la comunicación agente-editor, similar a cómo el Language Server Protocol (LSP) estandarizó la integración del servidor de idiomas. Los agentes que implementan ACP funcionan con cualquier editor compatible y los editores que admiten ACP obtienen acceso a todos los agentes compatibles con ACP.

---

## ¿Qué es ACP?

Los agentes y editores de codificación de IA están estrechamente vinculados sin un estándar. Cada editor debe crear integraciones personalizadas para cada agente, lo que genera una sobrecarga de integración, compatibilidad limitada y dependencia del desarrollador.

ACP resuelve esto proporcionando un protocolo estandarizado. Kiro CLI implementa ACP para que pueda usarse como agente de IA en cualquier editor compatible con ACP (JetBrains, Zed, etc.).

---

## Inicio rápido

Ejecute Kiro como agente ACP:
```golpecito
kiro-cli acp
```

Utilizá una configuración de agente específica:
```golpecito
kiro-cli acp --agente mi-agente
```

El agente se comunica a través de **stdin/stdout** usando **JSON-RPC 2.0**. Configure su editor para generar este comando.

---

## Configuración del editor

### General

Utilizá la **ruta completa** a `kiro-cli` en la configuración de su editor. Los IDE a menudo no heredan la RUTA de su shell, por lo que es posible que no se encuentren comandos como `kiro-cli`.

Encuentra el camino:
```golpecito
cual kiro-cli
# Comúnmente: ~/.local/bin/kiro-cli en Linux/macOS
```

### IDE de JetBrains

Configure a través de la configuración del **complemento JetBrains AI**. Agregue Kiro CLI como agente compatible con ACP utilizando la ruta completa.

### Zed

Configure en `~/.config/zed/settings.json` en la sección `assistant`. Establezca el comando en la ruta completa de `kiro-cli acp`.

### Otros editores

Cualquier editor que admita el protocolo ACP puede utilizar Kiro CLI. Consulte la documentación del editor específico para configurar los agentes ACP.

---

## Métodos ACP admitidos

Kiro CLI implementa la spec ACP que incluye:
- **Protocolo central**: gestión de sesiones, selección de modelos y transmisión de respuestas
- **Capacidades del agente**: acceso a herramientas, gestión de contexto y estado de conversación
- **Actualizaciones de sesiones**: transmisión en tiempo real de las respuestas de los agentes

---

## Extensiones Kiro

Kiro extiende ACP con métodos personalizados (con el prefijo `_kiro.dev/` según la spec de ACP) para exponer características específicas de Kiro:

- [Comandos de barra diagonal] (https://kiro.dev/docs/cli/reference/slash-commands)
- [eventos del servidor MCP] (https://kiro.dev/docs/cli/mcp)
- [Compactación de contexto](https://kiro.dev/docs/cli/chat#context-management)

Los clientes que no admiten estas extensiones pueden ignorarlas con seguridad: son mejoras opcionales.

> Nota: Estas extensiones son **experimentales** y están sujetas a cambios en futuras versiones.

---

## Almacenamiento de sesiones

Las sesiones se almacenan localmente y se pueden reanudar. El ID de sesión se incluye en las respuestas de ACP para permitir a los clientes hacer referencia a sesiones específicas.

## Registro

Utilizá el indicador `--log-level` para controlar la detalle del registro cuando se ejecuta en modo ACP. Los registros se escriben en stderr para evitar interferir con la comunicación JSON-RPC en stdout.