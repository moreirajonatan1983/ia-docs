#kiroignorar

> **Fuente:** [kiro.dev/docs/editor/kiroignore/](https://kiro.dev/docs/editor/kiroignore/)

---

`.kiroignore` usa patrones de estilo gitignore para controlar a qué archivos puede acceder Kiro. Esto le brinda un control preciso sobre lo que el agente de IA puede leer e interactuar en su proyecto.

---

## ¿Por qué utilizar .kiroignore?

| Razón | Descripción |
|---|---|
| **Seguridad** | Evite que Kiro acceda a archivos que contengan credenciales, claves API u otros datos confidenciales |
| **Privacidad** | Excluir información confidencial de las interacciones de IA |
| **Cumplimiento** | Asegúrese de que Kiro no acceda a archivos que no deberían compartirse con servicios externos |
| **Enfoque** | Mantenga relevante el contexto de Kiro excluyendo archivos grandes o creando artefactos |

---

## Configurar el espacio de trabajo Ignorar

Para excluir archivos en un proyecto específico:

1. Cree un archivo `.kiroignore` en la raíz de su proyecto (o cualquier subdirectorio)
2. Agregue patrones para los archivos que desea excluir:

```
# Secretos y credenciales
.env
.env.*
!.env.ejemplo
*.pem
*.clave

# Directorios privados
secretos/
privado/
```

3. Abra **Configuración** (`Cmd+` en Mac o `Ctrl+` en Windows/Linux)
4. Busque **Archivos ignorados por el agente** (configuración: `kiroAgent.agentIgnoreFiles`)
5. Agregue `.kiroignore` a la matriz

Kiro ahora omitirá cualquier archivo que coincida con sus patrones.

> **Consejo:** Comience con las credenciales y los secretos: estos son los archivos de mayor prioridad a proteger. Siempre puedes ampliar tus patrones a medida que evoluciona tu proyecto.

---

### Opciones de configuración

La configuración `kiroAgent.agentIgnoreFiles` acepta una variedad de nombres de archivos:

- Utilice varios tipos de archivos ignorados simultáneamente: `[".gitignore", ".kiroignore"]`
- Establezca en `[]` para deshabilitar los archivos ignorados a nivel del espacio de trabajo.

### Subdirectorio Ignorar archivos

Al igual que `.gitignore`, puedes colocar archivos `.kiroignore` en subdirectorios para anular o extender patrones de los directorios principales. **Los patrones en el subdirectorio ignoran los archivos tienen prioridad** para los archivos dentro de ese subdirectorio.

---

## Archivos de ignorar globalmente

Kiro respeta automáticamente los archivos ignorados globales si existen; no se necesita configuración:

- `~/.kiro/settings/kiroignore` — Tus patrones globales de ignorancia de Kiro (se aplica a todos los proyectos)
- Archivo de ignoración global de Git (configurado a través de `core.excludesfile` en tu configuración de git): solo se aplica en repositorios de git

---

## Sintaxis del patrón

`.kiroignore` usa **sintaxis estándar de gitignore**:

| Patrón | Significado |
|---|---|
| `archivo.txt` | Ignorar un archivo específico |
| `*.log` | Ignore todos los archivos con extensión `.log` |
| `carpeta/` | Ignorar un directorio completo |
| `**/temp` | Ignore `temp` en cualquier directorio |
| `! mantener.txt` | Volver a incluir un archivo previamente ignorado |

> **Nota:** No puede volver a incluir un archivo si se excluye un directorio principal. Por ejemplo, si ignora `secrets/`, agregar `!secrets/public.txt` no funcionará. Utilice patrones más específicos en lugar de excluir todo el directorio.

---

## Ejemplos

### Protección de claves y secretos API

```gitignorar
# Archivos de entorno con credenciales.
.env
.env.local
.env.producción

# Mantenga la plantilla accesible
!.env.ejemplo

# Archivos de certificado y clave
*.pem
*.clave
*.p12
credenciales/
```

### Excluyendo artefactos de compilación y archivos de datos

```gitignorar
# Construir salidas
dist/
construir/
.siguiente/

# Archivos de datos
*.sql
*.volcado
datos/exportaciones/
```

### Configuración de cumplimiento del equipo

```gitignorar
# Directorios de datos de clientes
datos-cliente/
pii/

# Documentos de auditoría y cumplimiento
cumplimiento/interno/
informes-de-auditoría/
```

> Utilice `.kiroignore` cuando necesite reglas diferentes para el acceso del agente frente al control de versiones, o para bloquear archivos que se rastrean en git pero que Kiro no debería leer.

---

## Mejores prácticas

- **Utilice comentarios** para documentar por qué se ignoran los archivos: útil para los miembros del equipo
- **Patrones de prueba** pidiéndole a Kiro que lea un archivo ignorado; indicará que el acceso está bloqueado
- **Revise los patrones periódicamente** a medida que evoluciona la estructura de su proyecto
- **Coordine con su equipo** patrones globales para lograr un comportamiento coherente en todos los espacios de trabajo.