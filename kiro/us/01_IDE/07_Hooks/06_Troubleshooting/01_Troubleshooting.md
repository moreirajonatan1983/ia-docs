# Troubleshooting Hooks

> **Source:** [kiro.dev/docs/hooks/troubleshooting/](https://kiro.dev/docs/hooks/troubleshooting/)

---

## Common Issues

### Hook Not Triggering

- **El file pattern no coincide:** Verificá que el pattern matchee los archivos objetivo
- **Hook deshabilitado:** Verificá que el hook esté habilitado (ícono de ojo en el panel)
- **Tipo de evento incorrecto:** Revisá que el Event seleccionado sea el correcto para tu caso

### Unexpected Hook Behavior

- **Instrucciones ambiguas:** Revisá las instrucciones del hook para mayor claridad
- **Hooks en conflicto:** Verificá si hay otros hooks que se disparan en el mismo evento
- **File patterns demasiado amplios:** Acotá los patterns a archivos más específicos

### Performance Issues

- **File patterns muy amplios:** Usá patterns más específicos para reducir el scope
- **Instrucciones complejas (Agent Prompt):** Simplificá las instrucciones del hook
- **Comando lento (Shell Command):** Asegurate de que el comando complete rápidamente
- **Demasiados trigger events:** Reducí la frecuencia de los eventos de disparo

---

## Debugging Tips

1. **Verificá el tipo de trigger** — Confirmá que el event type coincide con cuando esperás que corra el hook
2. **Testeá el file pattern** — Usá un pattern más amplio temporalmente para verificar que el hook se activa
3. **Revisá el panel de Output** — Buscá errores o mensajes de los hooks en ejecución
4. **Simplificá primero** — Empezá con un hook simple, confirmá que funciona, y luego agregá complejidad

---

## Related

- Para problemas más generales, consultá la [guía de troubleshooting principal →](../12_Troubleshooting.md)
- [Best practices →](./05_Best%20practices.md)
- [Hook Management →](./04_Management.md)