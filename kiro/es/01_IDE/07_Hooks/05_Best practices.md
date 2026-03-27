# Mejores prácticas de hook

> **Fuente:** [kiro.dev/docs/hooks/best-practices/](https://kiro.dev/docs/hooks/best-practices/)

---

## Diseño de hook

### Sea específico y claro
- Escribí instrucciones detalladas y sin ambigüedad para el agente
- Enfocá cada hook en **una sola tarea específica**
- Usa pasos numerados para operaciones complejas

### Pruebe a fondo
- Testeá hooks con escenarios de ejemplo antes de usarlos en producción
- Verifica que funcionan con casos extremos
- Para hooks relacionados con archivos, empezá con patrones de archivos limitados antes de expandir

### Supervisar el rendimiento
- Asegurate de que los hooks no ralenticen tu flujo de trabajo
- Considerá la frecuencia de los eventos desencadenantes
- Optimizá los indicadores de eficiencia.

---

## Consideraciones de seguridad

### Validar entradas
- Asegurate de que los hooks manejen contenido inesperado con gracia
- Considerará posibles casos extremos
- Testeá con entrada malformada o inesperada

### Limitar el alcance
- Para hooks relacionados con archivos, puntúe a tipos de archivo o directorios específicos cuando sea posible
- Usá patrones de archivos precisos para evitar ejecuciones innecesarias
- Considerará el impacto de los hooks en todo el código base.

### Revisar periódicamente
- Actualizá la lógica del hook a medida que el proyecto evoluciona
- Elimina los hooks que ya no sean necesarios
- Refina los avisos basándote en los resultados reales

---

## Colaboración en equipo

### Hooks para documentos
- Mantené documentación clara del propósito de cada hook.
- Incluye ejemplos del comportamiento esperado.
- Documentación de limitaciones de casos extremos

### Compartir configuraciones
- Usá hooks consistentes entre todos los miembros del equipo
- Almacená las configuraciones de hooks en control de versiones (`.kiro/hooks/`)
- Crea hooks estándar para flujos de trabajo comunes del equipo

### Integración del control de versiones
- Considerá hooks que se integran con tu sistema de control de versiones
- Crea hooks para flujos de trabajo de revisión de código.
- Usá hooks para hacer cumplir los estándares del equipo

---

## Referencia rápida: Shell frente a indicador del agente

| Situación | Usar |
|---|---|
| Linting, formato, scripts determinísticos | **Comando Shell** (más rápido, sin créditos) |
| Revisión, análisis, generación de contenido | **Agent Prompt** (contextual, consumir créditos) |
| Validación precompromiso | **Comando Shell** |
| Sugerencias de código | **Aviso del agente** |