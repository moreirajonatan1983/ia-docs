# Modo tangente

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#tangent-mode)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

## Descripción general

Tangent Mode permite crear **puntos de control de conversación** para explorar temas secundarios sin interrumpir el flujo principal de la conversación.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableTangentMode verdadero
```

**Activar:** `/tangente` o `Ctrl+T`

---

## Características

- Crear puntos de control de conversación.
- Explorar temas tangenciales
- Volver al hilo principal de conversación
- Preservar el contexto de la conversación.

---

## Cómo funciona

```
> Estoy implementando autenticación con JWT...
> /tangent # o Ctrl+T — crea un punto de control aquí

[tangente] > ¿Cuál es la diferencia entre RS256 y HS256?
[tangente] > ¿Cuándo usar cada uno?

> /tangent # vuelve al punto de control anterior

> Continuando con JWT... (contexto preservado)
```

---

## Casos de uso

- Hacer preguntas de contexto sin perder el hilo principal
- Explorar alternativas antes de comprometerse con un enfoque
- Investigar un error sin contaminar la conversación principal
- Aprender sobre una tecnología mientras trabajas en otra tarea

---

## Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos del modo tangente completo →](https://kiro.dev/docs/cli/experimental/tangent-mode)