# Skills del agente

> **Fuente:** [kiro.dev/docs/cli/skills/](https://kiro.dev/docs/cli/skills/)

---

Los Agent Skills son paquetes portátiles de instrucciones que se activan automáticamente cuando tu solicitud coincide con su descripción. Son similares a los Steering Files pero **on-demand** — Kiro solo los carga cuando son necesarios.

---

## Cómo funcionan las skills

Al iniciar una sesión de chat, Kiro descubre las skills disponibles leyendo sus nombres y descripciones. Cuando tu solicitud coincide con la descripción de una skill, Kiro carga automáticamente las instrucciones completas y las sigue.

```
> Review this PR for security issues
[skill: pr-review activated]
I'll review the PR using the security checklist...
```

Las skills **se activan automáticamente** según tu solicitud. No hay comando de barra diagonal para invocarlos: Kiro decide cuándo una skill es relevante comparando tu solicitud contra las descripciones de las skills.

Para ver qué skills están disponibles en tu sesión actual:

```
> /context show
```

---

## Ubicaciones de skills

Las skills pueden almacenarse en dos lugares:

| Ubicación | Alcance |
|---|---|
| `.kiro/skills/` | **Workspace** — Solo para ese proyecto |
| `~/.kiro/skills/` | **Global** — Disponible en todos los Workspaces |

Cuando las skills comparten el mismo nombre, **las skills del Workspace tienen prioridad** sobre los globales.

### Agente predeterminado

El agente por defecto (`kiro_default`) carga automáticamente todos los skills en `.kiro/skills/` y `~/.kiro/skills/`.

### Agentes personalizados

Los agentes personalizados requieren que especifiques explícitamente las skills en su configuración usando el protocolo `skill://`:

```json
{
  "resources": ["skill://pr-review", "skill://cdk-deploy"]
}
```

---

## Creando una skill

Un Skill es una **carpeta** que contiene un archivo `SKILL.md`:

```
pr-review/
├── SKILL.md         # Requerido
└── references/      # Opcional
    └── checklist.md
```

### Formato SKILL.md

El archivo empieza con **YAML frontmatter** seguido de instrucciones en Markdown:

```markdown
---
nombre: pr-revisión
Descripción: revise las pull requests para determinar la calidad del código, los problemas de seguridad y la cobertura de las pruebas. Úselo al revisar Pull Requests o preparar código para revisión.
---

## Revisar la lista de verificación
Al revisar una pull request:
1. Verifique vulnerabilidades, riesgos de inyección y secretos expuestos.
2. Verificar que se manejen los casos extremos y los modos de falla
3. Confirme que el nuevo código tenga las pruebas adecuadas.
4. Asegúrese de que las variables y funciones tengan nombres claros

## Problemas comunes a señalar
- Credenciales codificadas o claves API
- Falta validación de entrada
- Rechazos de promesas no controlados
- Declaraciones Console.log dejadas en el código de producción.
```

### Campos frontales

| Campo | Descripción |
|---|---|
| `nombre` | Identificador único del Skill |
| `descripción` | **Crítico** — Determina cuándo se activa. Incluir palabras clave y acciones específicas. |

### Archivos de referencia

Para documentación extensa, use una carpeta `references/`:

```
aws-deployment/
├── SKILL.md
└── references/
    ├── ecs-guide.md
    └── troubleshooting.md
```

Referencia los archivos desde `SKILL.md`:

```markdown
For ECS deployments, follow the guide in `references/ecs-guide.md`.
```

Kiro carga los archivos de referencia **solo cuando las instrucciones lo indican**.

---

## Ejemplo completo: skill de implementación de CDK

```
cdk-deploy/
├── SKILL.md
└── references/
    └── stack-patterns.md
```

**SKILL.md:**
```markdown
---
nombre: implementación de cdk
Descripción: Implemente pilas de AWS CDK con las mejores prácticas. Úselo al implementar infraestructura, ejecutar cdk implementar o solucionar problemas de CDK.
---

## Flujo de trabajo de implementación
1. Ejecute `cdk synth` para validar las plantillas antes de implementarlas.
2. Utilizá `cdk diff` para obtener una vista previa de lo que cambiará
3. Ejecute `cdk implementar` y revise los cambios de IAM

## Comprobaciones previas al despliegue
- Verifique que las credenciales de AWS estén configuradas para la cuenta de destino
- Verificar que la versión CDK coincida con los requisitos del proyecto.
- Revise `references/stack-patterns.md` para conocer patrones específicos del entorno

## Procedimiento de reversión
Si la implementación falla:
1. Verifique la consola de CloudFormation para ver el error específico.
2. Ejecute `cdk destroy` solo si la pila está en un estado fallido
3. Solucione el problema y vuelva a implementar
```

**Uso:**
```
> Implementar mi pila CDK en preparación
[skill: cdk-deploy activado]
Seguiré el flujo de trabajo de implementación. Primero, déjame sintetizar las plantillas...
```

---

## Mejores prácticas

- **Descripciones precisas** — La descripción determina la activación. Ejemplos:
  - ✅ `Revisar las pull requests para detectar vulnerabilidades de seguridad. Úselo al revisar las Pull Requests.`
  - ❌ `Ayuda con la revisión del código`
- **SKILL.md accionable** — Poné el material de referencia detallado en `references/`
- **Elegí el alcance correcto** — Skills globales para flujos de trabajo personales; Workspace para procedimientos de equipo
- **Versión de control** — Commitá `.kiro/skills/` a tu repositorio para que todo el equipo comparta los flujos de trabajo

---

## Relacionado

- [Steering →](./06_Steering.md) — Contexto y convenciones del proyecto
- [Agentes personalizados →](./04_Custom%20agents/) — Configuración de agentes y recursos
- [ACP →](./08_ACP.md) — Protocolo de cliente agente