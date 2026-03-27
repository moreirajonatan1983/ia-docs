# Herramienta de pensamiento

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#thinking-tool)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

## Descripción general

El Thinking Tool muestra el **proceso de pensamiento de la IA** para problemas complejos, con procesos de pensamiento paso a paso visibles para el usuario.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enablePensando verdadero
```

---

## Características

- Proceso de toma de decisiones transparente
- Visualización del razonamiento paso a paso
- Útil para depuración y aprendizaje
- Mejor comprensión de las conclusiones del agente

---

## Salida de ejemplo

```
> ¿Por qué mi API devuelve 401 incluso con un token válido?

[pensando]
1. El usuario tiene un token válido pero obtiene 401.
2. Posibles causas:
   - Formato del token incorrecto (falta el prefijo del portador)
   - Token caducado
   - Algoritmo de firma incorrecto
   - El nombre del encabezado no coincide
3. Es necesario verificar: configuración del middleware, lógica de validación del token
[/pensando]

Al observar su código, es probable que el problema esté en el middleware...
```

---

## Casos de uso

- **Complejo de depuración** — Ver cómo el agente analiza el problema
- **Aprendizaje** — Entender el razonamiento detrás de las decisiones
- **Validación** — Verificar que el agente está considerando los factores correctos
- **Arquitectura** — Evaluar trade-offs en decisiones de diseño

---

## Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos completos de la herramienta de pensamiento →](https://kiro.dev/docs/cli/experimental/thinking)