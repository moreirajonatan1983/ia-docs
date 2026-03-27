# Hooks de solución de problemas

> **Fuente:** [kiro.dev/docs/hooks/troubleshooting/](https://kiro.dev/docs/hooks/troubleshooting/)

---

## Problemas comunes

### El hook no se activa

| Posible causa | Solución |
|---|---|
| El patrón del archivo no coincide | Verificá que el patrón coincide con los archivos objetivo |
| hook deshabilitado | Verifique que el hook esté habilitado (ícono de ojo en el panel) |
| Tipo de evento incorrecto | Revisa que el Evento seleccionado sea el correcto para tu caso |

### Comportamiento inesperado del hook

| Posible causa | Solución |
|---|---|
| Instrucciones ambiguas | Revisá las instrucciones del hook para mayor claridad |
| Hooks en conflicto | Verificá si hay otros hooks que se disparan en el mismo evento |
| Patrones de archivos demasiado amplios | Acotá los patrones a archivos más específicos |

### Problemas de rendimiento

| Posible causa | Solución |
|---|---|
| Patrones de archivos muy amplios | Usamos patrones más específicos para reducir el alcance |
| Instrucciones complejas (Agent Prompt) | Simplificá las instrucciones del hook |
| Comando lento (Comando Shell) | Asegurate de que el comando se complete rápidamente |
| Demasiados desencadenan acontecimientos | Reduzca la frecuencia de los eventos de disparo |

---

## Consejos de Debug

1. **Verificá el tipo de trigger** — Confirmá que el tipo de evento coincide con cuando esperes que corra el hook
2. **Testeá el patrón de archivo** — Utilizá un patrón más amplio temporalmente para verificar que el hook se activa
3. **Revisá el panel de Output** — Buscá errores o mensajes de los hooks en ejecución
4. **Simplificá primero** — Empezá con un hook simple, confirma que funciona, y luego agrega complejidad

---

## Relacionado

- Para problemas más generales, consulte la [guía de solución de problemas principal →](../12_Troubleshooting.md)
- [Mejores prácticas →](./05_Best%20practices.md)
- [Gestión de hooks →](./04_Management.md)