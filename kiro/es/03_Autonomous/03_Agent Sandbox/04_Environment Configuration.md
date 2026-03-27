# Configuración del entorno: Agente Sandbox

> **Fuente:** [kiro.dev/docs/autonomous-agent/sandbox/environment-configuration/](https://kiro.dev/docs/autonomous-agent/sandbox/environment-configuration/)

---

El sandbox del Agente Autónomo puede configurarse usando un `Dockerfile` para que el entorno coincida exactamente con los requisitos de tu proyecto.

---

## Configuración automática

Kiro Autónoma Agent busca un `Dockerfile` en la **raíz de tu repositorio**. Si lo encuentra, el agente configura automáticamente el sandbox basándose en esas Specs.

> **Limitación:** Solo se soportan imágenes de contenedores **disponibles públicamente**. Las imágenes de registros privados y repositorios privados no pueden ser accedidas por el sandbox.

---

## Configuración del archivo Docker

Podés usar un [Dockerfile](https://docs.docker.com/reference/dockerfile/) estándar para configurar el entorno del sandbox. El agente construirá y usará la imagen Docker definida en tu Dockerfile.

### Ejemplo de archivo Docker

```archivo docker
DESDE el nodo:18

DIRTRABAJO /aplicación

# Instalar dependencias
COPIAR paquete*.json ./
EJECUTAR instalación npm

# Copiar el código de la aplicación
COPIAR. .

# Establecer variables de entorno
ENV NODE_ENV=producción

# Exponer puerto
EXPONER 3000

# Comando de inicio
CMD ["npm", "inicio"]
```

---

## Casos de uso

- Asegurar que las mismas versiones de herramientas y runtimes están disponibles en las tareas del agente
- Preinstalar dependencias del sistema (librerías nativas, compiladores, etc.)
- Configurar el entorno de compilación exacto que usa tu aplicación
- Reproducir condiciones específicas necesarias para correr pruebas.

---

## Relacionado

- [MCP en Sandbox →](./03_MCP.md)
- [Variables de entorno →](./02_Environment%20Variables.md)
- [Acceso a Internet →](./01_Internet%20Access.md)
- [Integración de GitHub →](../04_GitHub.md)