# Install Powers

> **Source:** [kiro.dev/docs/powers/](https://kiro.dev/docs/powers/) · [kiro.dev/powers](https://kiro.dev/powers)

---

## What are Powers?

Powers son bundles que combinan **MCP servers + steering + hooks**, activados dinámicamente según el contexto de tu conversación. En lugar de cargar todos los MCP tools de golpe, los powers se activan solo cuando son relevantes.

### El problema: context overload

| Sin Powers | Con Powers |
|---|---|
| Conectar 5 MCP servers carga 100+ tool definitions antes de tu primer prompt | Los tools se cargan **on-demand** basado en keywords de la conversación |
| 5 servers pueden consumir 50,000+ tokens (40% del context window) | Solo se carga lo relevante al task actual |
| Sin contexto del framework, el agente adivina | Acceso instantáneo a conocimiento especializado |

### How Powers Work

Cuando iniciás una tarea, Kiro:
1. Lee la descripción de la tarea
2. Evalúa los powers instalados contra el task
3. Carga **solo** los powers relevantes en contexto

### What's in a Power?

| Componente | Descripción |
|---|---|
| `POWER.md` | Archivo de steering que describe al agente qué MCP tools tiene disponibles y cuándo usarlos |
| MCP server config | Tools y detalles de conexión al MCP server |
| Steering / Hooks | Tareas automatizadas en eventos del IDE o slash commands (opcional) |

**Ejemplo:** Instalás el Stripe power. Cuando mencionás "payment" o "checkout", el power se activa — cargando los MCP tools de Stripe y el `POWER.md`. Cuando pasás a trabajar con la base de datos, el Supabase power se activa y Stripe se desactiva.

---

## Marketplace Partners

Powers curados de socios oficiales disponibles con un clic:

`Datadog` · `Dynatrace` · `Figma` · `Neon` · `Netlify` · `Postman` · `Supabase` · `Stripe` · `Strands SDK` · `AWS Aurora`

---

## Installing a Power

### From the Marketplace (one-click)

1. Abrí el panel **Powers** en Kiro
2. Explorá los powers disponibles en [kiro.dev/powers](https://kiro.dev/powers)
3. Hacé clic en **Install** — el power se registra automáticamente
4. No requiere configuración manual de JSON ni setup por línea de comandos

### From GitHub

1. Abrí el panel **Powers** en Kiro
2. Seleccioná **Add power from GitHub**
3. Pegá la URL del repositorio público del power
4. Kiro descarga e instala el power automáticamente

### From Local Path

1. Abrí el panel **Powers** en Kiro
2. Seleccioná **Add power from Local Path**
3. Seleccioná el directorio de tu power local
4. Ideal para testear powers propios antes de publicarlos

---

## Next Steps

- [Create your own power →](./02_Create powers.md)
- [Explore marketplace →](https://kiro.dev/powers)