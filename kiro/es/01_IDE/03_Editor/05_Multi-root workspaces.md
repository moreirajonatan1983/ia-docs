# Workspaces Multi-Raíz (Multi-root)

> **Fuente:** [kiro.dev/docs/editor/multi-root-workspaces/](https://kiro.dev/docs/editor/multi-root-workspaces/)

---

Los *workspaces* multi-raíz te permiten sostener 12 proyectos diferentes tirados sobre una única ventana de Kiro en modo Dios. Todas las funcionalidades y razonamientos impulsados por inteligencia artificial que ofrece la herramienta están preparados para sobrevivir sin fallos saltando de forma inteligente entre esos repositorios/carpetas raíz.

---

## Funcionalidad principal

Kiro resuelve las rutas locales e importaciones de manera automática cruzando carpetas raíz, permitiéndote navegar tu coloso Frankenstein sin problemas de dependencias engañosas.

La **[Indexación inteligente](https://kiro.dev/docs/editor/codebase-indexing/)** y los *Repository Maps* logran convivir gloriosamente en escenarios muti-raíz: Ambos mapeos consolidados terminan conteniendo la mezcla de todas las raíces como un enorme bloque, dándote la libertad de pedirle a la IA algo como "#File1.tsx (raíz A) vinculate con #File2.py (raíz B)" tal como harías si solo tuvieras un proyectito.

Al vincular manualemente un archivo en el chat usando `#file`, y detectarse que existen 15 archivos "index.tsx" repartidos en cada raíz individual, Kiro te va a armar un desplegable visual mostrándote explícitamente el origen de cada uno para que piques el correcto y no le arruines la vida resolviendo.

---

## Specs (Specs)

Kiro carga agresivamente todos los archivos de [Specs](https://kiro.dev/docs/specs/) desenterrándolos desde el submundo `.kiro` ubicado individualmente en **cada** raíz de tu espacio gigante, mostrando una lista unificada espectacular en el panel. Lado a lado de cada Spec dice a qué proyecto (carpeta raíz) pertenece la criatura.

- Podés forzar sutilmente a Kiro a laburar en el Spec de una de las carpetas desde otra distinta.
- Cuando trates de parir un Spec nuevo de 0, el menú te rogará gentilmente que escojas dónde pretendés guardarlo.

---

## Archivos de Steering

Misma lógica: Kiro absorbe los archivos de [Steering](https://kiro.dev/docs/steering/) que habitan las carpetas `.kiro/` de cada módulo o proyecto, y las lista colapsadas bajo el título **Agent Steering** dentro de un bloque maestro llamado *Workspace*. De nuevo, visualmente te advierte de qué raíz salió cada regla.

| Comportamiento | Lógica |
|---|---|
| **Inclusión estricta** | El Steering se le inyecta al Agente obligatoriamente sin importar en qué carpeta ande modificando cosas. |
| **Inclusión condicional** | Solo le impacta temporalmente al Agente si detecta que la víctima que está operando en su turno actual coincide con la carpeta dueña del archivo Steering. |

A la hora de crear una regla de Steering grupal vos también serás apuntado por Kiro pidiéndote confirmar obligatoriamente dónde meter el script.

---

## Hooks (hooks de automatización)

El rastreador se encarga de ubicar cada uno de los [hooks configurados](https://kiro.dev/docs/hooks/) bajo el capó de la subcarpeta `.kiro` en cada monstruo multi-proyecto que insertes en la UI, uniéndolo al panel **Agent Hooks**.

> **Importantísimo:** Los hooks puristas como Crear, Eliminar o Guardar archivos **saltan al ataque (triggers) estrictamente** cuando el Agente Kiro osa manipular el terreno y los bits exclusivos de la raíz de la que partió ese hook. No se cruzan los cables con otras raíces vecinas de la ventana para evitar apocalipsis asíncronos en cadena.

A la de crear un trigger, se asume que debés asignarle una cama raíz obligada.

---

## Servidores MCP

Las configuraciones globales de [servidores MCP](https://kiro.dev/docs/mcp/) en cada micro-raíz en un multi-root se unen pacíficamente al levantar Kiro:

- Carga masiva paralela de todas las definiciones de MCP dispersas apenas inicia.
- Regla letal por conflicto: si a los 2 proyectos se les ocurrió llamar "api-local" a un Server MCP, la que prevalece al invocar y aplasta a la otra es **la última configuración leída en orden alfabético**.
- Los servers inicializados se arrancan asumiendo como origen de *working-directory* el camino maestro de la **primera carpeta raíz** que abriste.

> Si tenés ganitas de tocar el **Open MCP Settings**, la que abría de buenas a primeras es tu macro-configuración humana y no la del proyecto. Si apretás el botón de **Workspace settings** en un mega-proyecto, de vuelta el IDE se colgará gentilmente a preguntarte para quién creés que venís a cambiar cosas.