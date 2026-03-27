# Agentes personalizados - Kiro CLI

> **Fuente:** [kiro.dev/docs/cli/custom-agents/](https://kiro.dev/docs/cli/custom-agents/)

---

Los agentes personalizados le permiten crear e implementar agentes de IA especializados adaptados a flujos de trabajo específicos, con un control detallado sobre las herramientas, el contexto y el comportamiento.

---

## Beneficios de utilizar agentes personalizados

1. **Optimización del flujo de trabajo**: cree agentes adaptados a tareas específicas como administración de infraestructura de AWS, revisiones de código o sesiones de depuración.
2. **Reducción de interrupciones**: apruebe previamente herramientas confiables para eliminar las solicitudes de permiso durante las sesiones de trabajo enfocadas.
3. **Contexto mejorado**: incluya automáticamente documentación relevante del proyecto, archivos de configuración o información del sistema.
4. **Colaboración en equipo**: comparta configuraciones de agentes personalizadas con los miembros del equipo para garantizar entornos de desarrollo consistentes.
5. **Control de seguridad**: limite el acceso a las herramientas solo a lo necesario para flujos de trabajo específicos, lo que reduce los posibles riesgos de seguridad.

---

## Relación con MCP y herramientas integradas

Los agentes personalizados trabajan tanto con herramientas integradas como con herramientas externas proporcionadas a través del Protocolo de contexto modelo (MCP):

- **Utilice herramientas integradas**: operaciones de archivos, ejecución de comandos, integración de AWS CLI y otras funciones principales
- **Integrar servidores MCP**: agregue herramientas y servicios personalizados a través de configuraciones de servidor MCP
- **Control de acceso a herramientas**: especifique exactamente qué herramientas de cada fuente están disponibles
- **Administrar conflictos de herramientas**: use alias para manejar conflictos de nombres entre diferentes fuentes de herramientas

---

## Próximos pasos

- [Creando agentes personalizados →](https://kiro.dev/docs/cli/custom-agents/creating/)
- [Referencia de configuración del agente →](https://kiro.dev/docs/cli/custom-agents/configuration-reference/)
- [Agentes compartidos →](https://kiro.dev/docs/cli/custom-agents/sharing/)