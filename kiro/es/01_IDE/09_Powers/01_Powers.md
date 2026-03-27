# Powers

> **Fuente:** [kiro.dev/docs/powers/](https://kiro.dev/docs/powers/)

---

Los Powers son paquetes dinámicos de contexto y herramientas MCP que le brindan a su agente de IA experiencia instantánea para cualquier marco o herramienta, cargando solo lo que es relevante, solo cuando es necesario.

---

## Empezar

- [Explorar Powers](https://kiro.dev/powers): explore Powers seleccionados de socios de lanzamiento e instálelos con un solo clic
- [Instalar un poder →](https://kiro.dev/docs/powers/installation/)
- [Crear un poder →](https://kiro.dev/docs/powers/create/)

---

## Concepto

### El problema: sobrecarga de contexto

Los agentes de IA se enfrentan a dos desafíos opuestos:

**Sin contexto marco, los agentes suponen.**
Su agente puede llamar a las API de Stripe, pero ¿sabe utilizar claves idempotentes? Puede consultar Neon, pero ¿comprende la agrupación de conexiones sin servidor? Sin experiencia incorporada, usted debe leer la documentación manualmente y refinar los enfoques hasta que el resultado sea el correcto.

**Con demasiado contexto, los agentes se ralentizan.**
Conecte cinco servidores MCP y su agente cargará más de 100 definiciones de herramientas antes de escribir una sola línea de código. Cinco servidores pueden consumir más de 50 000 tokens (el 40 % de su ventana de contexto) antes de su primer mensaje. Más herramientas deberían significar mejores resultados, pero el contexto no estructurado abruma al agente, lo que genera respuestas más lentas y resultados de menor calidad.

---

### Cómo funcionan los Powers

En lugar de cargar todas las herramientas MCP a la vez, los Powers **se activan dinámicamente según las palabras clave** en su conversación.

Cuando comienzas una tarea, Kiro:
1. Lee la descripción de la tarea.
2. Evalúa las potencias instaladas frente a la tarea
3. Carga **solo Powers relevantes** en contexto

Cuando mencionas "pago" o "pago", el poder de Stripe se activa, cargando las herramientas MCP de Stripe y la dirección POWER.md en contexto. Cuando pasas al trabajo de la base de datos, el poder de Supabase se activa y Stripe se desactiva.

---

### ¿Qué hay en un poder?

Un poder es un paquete unificado que incluye:

| Componente | Descripción |
|---|---|
| `PODER.md` | Archivo de Steering que le indica al agente qué herramientas MCP tiene disponibles y cuándo usarlas |
| **Configuración del servidor MCP** | Herramientas y detalles de conexión para el servidor MCP |
| **Dirección/hooks** *(opcional)* | Tareas automatizadas que se ejecutan en eventos IDE o mediante comandos de barra diagonal |

---

### ¿Qué hace que los Powers sean diferentes?

| Característica | Descripción |
|---|---|
| **Carga dinámica de herramientas MCP** | Los servidores MCP tradicionales cargan todas las herramientas por adelantado. Potencia las herramientas de carga bajo demanda, lo que reduce el uso del contexto básico y al mismo tiempo brinda a su agente acceso a docenas de tecnologías |
| **Ecosistema abierto** | Explore Powers seleccionados de socios de lanzamiento, incluidos Datadog, Dynatrace, Figma, Neon, Netlify, Postman, Supabase, Stripe, Strands SDK y AWS Aurora. Instale Powers creados por la comunidad desde las URL de GitHub o cree y comparta los suyos propios |
| **Instalación con un clic** | Explora Powers directamente en Kiro o en kiro.dev. Hacé clic en "Instalar" y la energía se registrará automáticamente. Sin archivos de configuración JSON, sin configuración de línea de comandos |

---

## Powers del socio de lanzamiento

| Socio | Caso de uso |
|---|---|
| **Stripe** | Pagos, suscripciones, facturación |
| **Supabase** | Base de datos PostgreSQL, autenticación, almacenamiento |
| **Neon** | PostgreSQL sin servidor |
| **Figma** | Tokens de diseño, Specs de componentes |
| **AWS Aurora** | Base de datos relacional administrada |
| **Netlify** | Implementación de frontend, funciones de borde |
| **Postman** | Pruebas y documentación de API |
| **Datadog** | Monitoreo, registros, APM |
| **Dynatrace** | Plataforma de observabilidad |
| **Strands SDK** | Desarrollo de agentes |