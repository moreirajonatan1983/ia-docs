# Modelos — Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/models/](https://kiro.dev/docs/cli/models/)

---

Kiro CLI admite los mismos modelos que el IDE. Consulte la [página de modelos IDE] (../../01_IDE/02_Models.md) para obtener los detalles completos del modelo, la tabla de comparación, las diferencias de comportamiento y las mejores prácticas.

---

## Comparación rápida

El costo es relativo a **Automático (1,0 veces el valor de referencia)**. Por ejemplo, una tarea que cuesta 10 créditos en Auto costaría 22 créditos en Opus, 4 créditos en Haiku o 0,5 créditos en Qwen3 Coder Next.

| Modelo | Mejor para | Costo |
|---|---|---|
| **Automático** *(recomendado)* | Uso general, mejor relación calidad/coste | 1,0x |
| **Claude Opus 4.6** | Codificación agente compleja, grandes bases de código | ~2,2x |
| **Claude Soneto 4.6** | Flujos de trabajo de desarrollo iterativos, canalizaciones multimodelo | ~1,0x |
| **Claude Haiku 4.5** | Iteraciones rápidas, conservación del crédito | ~0,4x |
| **MiniMax M2.5** | Ciclo de vida de desarrollo completo a bajo costo | 0,25x |
| **DeepSeek 3.2** | Flujos de trabajo agentes, generación de código | 0,25x |
| **MiniMax M2.1** | Programación multilingüe, generación de UI | 0,15x |
| **Qwen3 Coder Siguiente** | — | 0,5x |

---

## Cómo cambiar de modelo

### Desde la interfaz de chat

Utilice el menú desplegable de modelos en la interfaz de chat. Si no aparece un modelo, reinicie el cliente.

### Desde la línea de comando

Establecer un modelo específico como predeterminado:
```golpecito
configuración de kiro-cli chat.defaultModel claude-opus4.6
```

Guarde el modelo **actual** como predeterminado para todas las sesiones futuras (desde una sesión de chat):
```
> /modelo establecido-actual-como-predeterminado
```

Esto almacena su preferencia en `~/.kiro/settings/cli.json`. Las nuevas sesiones utilizan automáticamente este modelo.