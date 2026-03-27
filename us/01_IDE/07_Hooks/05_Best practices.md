# Hook Best Practices

> **Source:** [kiro.dev/docs/hooks/best-practices/](https://kiro.dev/docs/hooks/best-practices/)

---

## Hook Design

### Be Specific and Clear
- Escribí instrucciones detalladas y sin ambigüedad para el agente
- Enfocá cada hook en **una sola tarea específica**
- Usá pasos numerados para operaciones complejas

### Test Thoroughly
- Testeá hooks con escenarios de ejemplo antes de usarlos en producción
- Verificá que funcionan con edge cases
- Para hooks relacionados con archivos, empezá con file patterns limitados antes de expandir

### Monitor Performance
- Asegurate de que los hooks no ralenticen tu workflow
- Considerá la frecuencia de los trigger events
- Optimizá los prompts para eficiencia

---

## Security Considerations

### Validate Inputs
- Asegurate de que los hooks manejen contenido inesperado con gracefully
- Considerá posibles edge cases
- Testeá con input malformado o inesperado

### Limit Scope
- Para hooks relacionados con archivos, apuntá a tipos de archivo o directorios específicos cuando sea posible
- Usá file patterns precisos para evitar ejecuciones innecesarias
- Considerá el impacto de los hooks en todo el codebase

### Review Regularly
- Actualizá la lógica del hook a medida que el proyecto evoluciona
- Eliminá hooks que ya no sean necesarios
- Refiná los prompts basándote en los resultados reales

---

## Team Collaboration

### Document Hooks
- Mantené documentación clara del propósito de cada hook
- Incluí ejemplos del comportamiento esperado
- Documentá limitaciones o edge cases

### Share Configurations
- Usá hooks consistentes entre todos los miembros del equipo
- Almacená las configuraciones de hooks en control de versiones (`.kiro/hooks/`)
- Creá hooks estándar para workflows comunes del equipo

### Version Control Integration
- Considerá hooks que se integren con tu sistema de control de versiones
- Creá hooks para workflows de code review
- Usá hooks para enforcement de estándares del equipo

---

## Quick Reference: Shell vs. Agent Prompt

| Situación | Usar |
|---|---|
| Linting, formateo, scripts determinísticos | **Shell Command** (más rápido, sin créditos) |
| Revisión, análisis, generación de contenido | **Agent Prompt** (contextual, consume créditos) |
| Validación pre-commit | **Shell Command** |
| Sugerencias de código | **Agent Prompt** |