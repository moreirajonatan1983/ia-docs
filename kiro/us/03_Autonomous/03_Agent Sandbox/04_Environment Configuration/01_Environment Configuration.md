# Environment Configuration — Agent Sandbox

> **Source:** [kiro.dev/docs/autonomous-agent/sandbox/environment-configuration/](https://kiro.dev/docs/autonomous-agent/sandbox/environment-configuration/)

---

El sandbox del Autonomous Agent puede configurarse usando un `Dockerfile` para que el entorno coincida exactamente con los requisitos de tu proyecto.

---

## Automatic Configuration

Kiro Autonomous Agent busca un `Dockerfile` en la **raíz de tu repositorio**. Si lo encuentra, el agente configura automáticamente el sandbox basándose en esas especificaciones.

> **Limitación:** Solo se soportan imágenes de contenedores **disponibles públicamente**. Las imágenes de registros privados y repositorios privados no pueden ser accedidas por el sandbox.

---

## Dockerfile Configuration

Podés usar un [Dockerfile](https://docs.docker.com/reference/dockerfile/) estándar para configurar el entorno del sandbox. El agente construirá y usará la imagen Docker definida en tu Dockerfile.

### Example Dockerfile

```dockerfile
FROM node:18

WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy application code
COPY . .

# Set environment variables
ENV NODE_ENV=production

# Expose port
EXPOSE 3000

# Start command
CMD ["npm", "start"]
```

---

## Use Cases

- Asegurar que las mismas versiones de herramientas y runtimes están disponibles en las tareas del agente
- Pre-instalar dependencias del sistema (librerías nativas, compilers, etc.)
- Configurar el entorno de build exacto que usa tu aplicación
- Reproducir condiciones específicas necesarias para correr tests

---

## Related

- [MCP in Sandbox →](./03_MCP.md)
- [Environment Variables →](./02_Environment%20Variables.md)
- [Internet Access →](./01_Internet%20Access.md)
- [GitHub integration →](../04_GitHub.md)