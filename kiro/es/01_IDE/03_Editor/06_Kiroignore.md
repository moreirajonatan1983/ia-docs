# El archivo .kiroignore

> **Fuente:** [kiro.dev/docs/editor/kiroignore/](https://kiro.dev/docs/editor/kiroignore/)

---

Estructurar un `.kiroignore` imita el glorioso comportamiento base de `gitignore`, regulando como patovica a qué archivos tiene estúpidamente prohibido acceder el motor o IA de Kiro. Esto regala control total a nivel submolecular sobre la privacidad de la data que existe en tu *workspace*.

---

## ¿Por qué configurar tu .kiroignore?

| Motivo | Descripción |
|---|---|
| **Seguridad extrema** | Bloqueale totalmente el acceso a los `.env` o `.pem` llenos de credenciales en crudo, API keys de productivo y tokens robados. |
| **Privacidad** | Evitá que la IA mande en su contexto información PII (Datos de usuario personales) al intentar ayudar a programar módulos colindantes. |
| **Paz legal / Compliance** | Cumplí los ISO y normativas demostrando que el código fuente de tu agente local no sube secretos hacia los servidores frontera (OpenAi/Anthropic). |
| **Enfoque quirúrgico (Focus)** | Ahorrá toneladas de tokens y latencias evitando que el agente lea *build artifacts* y binarios insoportables (carpetas `dist`, o exportaciones tontas). |

---

## Cómo establecer reglas por proyecto (Workspace-level)

Bloquear cosas específicas es un trámite:

1. Creá un archivo desnudo llamado `.kiroignore` dentro de la raíz del proyecto (o hasta oculto dentro de tus subdirectorios si preferís).
2. Clavá adentro tus reglas sucias copiando lo asimilado de años de lidiar con gitignore:

```text
# Las joyitas y contraseñas de producción
.env
.env.*
!.env.example
*.pem
*.key

# Directorios blindados PII
secrets/
private/
```

3. Abrí en tu editor la configuración nativa (`Cmd+,` en macOS / `Ctrl+,` en Windows y Linux).
4. Buscá en el buscador general la opción **Agent Ignore Files** (o por su keyword interna `kiroAgent.agentIgnoreFiles`).
5. Cerciorate de agregar explícitamente `.kiroignore` metiéndolo al *array* principal o dejándolo marcado.

A partir de acá, Kiro cierra sus ojos a cualquier archivo o carpeta que cruce este umbral.

> **Punta del Iceberg:** Arrancá por barrer tus credenciales sí o sí. Eso es ley vital hoy en día en desarrollo. Con el paso del tiempo siempre podés robustecer las reglas viendo que basura temporal se queja el agente o qué indexa.

---

### Detalles técnicos avanzados (`kiroAgent.agentIgnoreFiles`)

Esta directiva oculta permite combinar escudos:

- Juntá todas las ignorancias: Podés decirle a `kiroAgent.agentIgnoreFiles` que lea `[".gitignore", ".kiroignore"]` de golpe. Dos pájaros, un tiro.
- Si le clavás el *array* liso de `[]`, rompés instantáneamente el escudo del workspace asumiendo plenos riesgos localmente.

### Sub-ignorancias anidadas

Tal cual lo harías con el mismísimo `.gitignore`, acá te pueden llover miles de archivos `.kiroignore` en varios cuartos o pasillos de tus directorios internos. **Los patrones escritos en un ignorador que se halle más enterrado en un sub-directorio ganan a los padres**, imponiendo una dictadura sobre esa carpeta puntual.

---

## Reglas Globales y supremas de rechazo

Kiro no nace estúpido, e internamente acata órdenes ignoradoras de configuraciones superiores en su disco de pura vocación predefinida:

- `~/.kiro/settings/kiroignore` — Tú mega patrón global para que aplique su dictadura oculta en todos y cada uno de los proyectos simultáneos donde abras tu IA (tus hábitos maestros).
- Archivo "Global Git Excludes" (si tenés `core.excludesfile` configurado hermosamente en tu bash). Este *hack* le sirve pero solo funciona activado dentro de un ecosistema git.

---

## Entendiendo la sintaxis

Si sabés `gitignore`, sentite cómodo acá. `.kiroignore` absorbe calcada su majestuosidad analítica:

| Patrón salvaje | Interpretación |
|---|---|
| `clave.txt` | Dispara el bloqueo asesino exclusivamente a tu archivo. |
| `*.log` | Cortale el rostro a todo rastro de debugeo insoportable que termine con punto log. |
| `build/` | Volá del mapa del universo de la IA cualquier archivo que pase dentro del reino de dicha carpeta entera. |
| `**/temp` | Le cerrás la cara a cualquier existencia llamada *temp*, escondida cuan profunda sea la madriguera del conejo. |
| `!example.env` | La mágica regla condicional salvadora: el comodín inverso obliga legalmente a volver a incluir al archivo reborrado por sentencias superiores. |

> **Warning para despistados:** El motor de comodín inverso NO revivirá un muertito si le eliminaste en la lista a su directorio entero superior. Es decir, si volaste a `secrets/` en la jerarquía alta, la expresión mágica rebelde de poner `!secrets/pulicito_api.txt` no tiene validez legal alguna y muere ignorada en llanto. Sean quirúrgicos, mis amigos.

---

## Recetas para tu día a día

### Escondiendo tu identidad frente al apocalipsis (Claves y API's)

```text
# Mi corazón vital
.env
.env.local
.env.production

# Pero por favor dejenle leer cómo iniciar mi servidor
!.env.example

# Mis pasaportes digitales
*.pem
*.key
*.p12
credentials/
```

### Volando basura artificial y reliquias pesadas

```text
# No es mágico, es RAM gastada
dist/
build/
.next/

# Nadie quiere esto en Kiro (Datos crudos pesados o extensiones ridículas)
*.sql
*.dump
data/exports/
```

### Cumpliendo con el fisco y la ética (Datos puramente ilegales)

```text
# Todo está censurado
client-data/
pii-storage/

# Lo que toca a los inversores escondido
legal/
compliance/internal/
audit-reports/
```

> **Consejo Sabio:** Usá este fichero a pura conciencia cuando exista la bifurcación enorme donde sí o sí, algo obligue a que un código le aplique subir a GitHub / Git remoto usando repositorios privados, pero no querés bajo ningun punto del planeta que el maldito modelo LLM lo procese cruzando la barrera de prompt/respuestas a la API.

---

## Buenas costumbres de experto (Best practices)

- **Comentá tus patologías:** A un año o inclusive en colaboraciones gruesas con juniors, dejá en texto en forma de block nota `# Esto lo tapo para no romper todo` al lado del bloqueo para que les sirva de faro a tu grupo.
- **Hackealo por la mala:** Probale la paciencia al Kiro Agente tirándole un prompt onda "¿Que dice el archivo secreto super mega loco.env?" a ver si tiene acceso y te jura que lo frenó un paredón invisible.
- **Recuentos semanales:** Revisar dos o tres veces con el equipo entero a la hora de encarar el inicio de reingeniería si vale la pena o no seguir bloqueando paths de *legacy*.
- **Paz mental corporativa:** Para arrancar parejo si arman una PyME o corporación interna, manden el global general idéntico emparejado en todos.