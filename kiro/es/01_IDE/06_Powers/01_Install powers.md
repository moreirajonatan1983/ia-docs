# Instalar poderes

> **Fuente:** [kiro.dev/docs/powers/](https://kiro.dev/docs/powers/) · [kiro.dev/powers](https://kiro.dev/powers)

---

## ¿Qué son los poderes?

Powers son paquetes que combinan **servidores MCP + dirección + hooks**, activados dinámicamente según el contexto de tu conversación. En lugar de cargar todas las herramientas de golpe MCP, los poderes se activan solo cuando son relevantes.

### El problema: sobrecarga de contexto

| Poderes del pecado | Poderes estafadores |
|---|---|
| Conectar 5 servidores MCP carga más de 100 definiciones de herramientas antes de tu primer aviso | Las herramientas se cargan **on-demand** basado en palabras clave de la conversación |
| 5 servidores pueden consumir 50.000+ tokens (40% de la ventana de contexto) | Solo se carga lo relevante al task actual |
| Sin contexto del framework, el agente adivina | Acceso instantáneo a conocimiento especializado |

### Cómo funcionan los poderes

Cuando inició una tarea, Kiro:
1. Lee la descripción de la tarea
2. Evalúa los poderes instalados contra el task
3. Carga **solo** los poderes relevantes en contexto

### ¿Qué hay en un poder?

| Componente | Descripción |
|---|---|
| `PODER.md` | Archivo de Steering que describe al agente qué herramientas MCP tienen disponibles y cuándo usarlas |
| Configuración del servidor MCP | Herramientas y detalles de conexión al servidor MCP |
| Dirección / Hooks | Tareas automatizadas en eventos del IDE o comandos de barra (opcional) |

**Ejemplo:** Instala el Stripe power. Cuando mencionás "pago" o "pago", el power se activa — cargando las herramientas MCP de Stripe y el `POWER.md`. Cuando pases a trabajar con la base de datos, el Supabase power se activa y Stripe se desactiva.

---

## Socios del mercado

Poderes curados de socios oficiales disponibles con un clic:

`Datadog` · `Dynatrace` · `Figma` · `Neon` · `Netlify` · `Postman` · `Supabase` · `Stripe` · `Strands SDK` · `AWS Aurora`

---

## Instalación de una fuente de alimentación

### Desde Marketplace (un clic)

1. Abrí el panel **Powers** en Kiro
2. Explora los poderes disponibles en [kiro.dev/powers](https://kiro.dev/powers)
3. Haz clic en **Instalar** — el poder se registra automáticamente
4. No requiere configuración manual de JSON ni configuración por línea de comandos

### De GitHub

1. Abrí el panel **Powers** en Kiro
2. Seleccioná **Añadir potencia desde GitHub**
3. Pegá la URL del repositorio público del power
4. Kiro descarga e instala el poder automáticamente

### Desde la ruta local

1. Abrí el panel **Powers** en Kiro
2. Seleccioná **Agregar energía desde la ruta local**
3. Selecciona el directorio de tu power local
4. Ideal para testear poderes propios antes de publicarlos

---

## Próximos pasos

- [Crea tu propio poder →](./02_Create powers.md)
- [Explorar el mercado →](https://kiro.dev/powers)