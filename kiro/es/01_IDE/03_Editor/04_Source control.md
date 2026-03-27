# Control de versiones

> **Fuente:** [kiro.dev/docs/editor/source-control/](https://kiro.dev/docs/editor/source-control/)

---

Kiro eleva tu flujo de trabajo de Git encargándose de autogenerar tus mensajes de *commit* (propulsados por IA) e integrándose perfecto en tu control de versiones actual.

---

## Generación de mensajes de commit

![Git Commit Message](https://kiro.dev/videos/git-commit-message.mp4)

Kiro puede observar tus cambios *staged* (preparados) y armar inteligentemente mensajes descriptivos siguiendo el formato estándar de la industria [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

### Cómo generar mensajes de commit

1. **Staggeá (prepará) tus cambios** desde el panel de Source Control oficial.
2. Hacé clic en el iconito de **🪄 varita mágica** justo arriba del cuadro de texto del mensaje.
3. **Revisá el mensaje:** Kiro analizará tus *diffs* y creará un mensaje bien robusto de la nada.
4. **Editalo:** Siempre vas a poder retocar el mensaje a tu manera o quitar lo que sobre.
5. **Aceptalo y committeá** tus cambios.

> **Tip:** Podés bindear tu propio atajo de teclado para la acción `Kiro: Generate Commit Message` desde la configuración de tus atajos (`Keyboard Shortcuts`) para ir a los pedos.

---

### Formato esperado

Kiro formatea siguiendo las **reglas de Conventional Commits**:

```text
<type>(<scope>): <subject>
- Primer cambio puntual detallado
- Segundo cambio fuerte o mejoras
- Tercer cambio (si aplica)
- De ser necesario, una explicación de por qué fue necesario un refactor
```

### Tipos de commits convencionales (NO traducir)

Estos prefijos están en inglés internacional para garantizar un control de versiones semántico:

| Tipo | Descripción estándar |
|---|---|
| `feat` | Implementación de características o funciones nuevas |
| `fix` | Reparación de defectos o *bugs* confirmados |
| `docs` | Modificación a los archivos documentales (README, manuales) |
| `style` | Modificaciones estéticas (espacios, saltos, comas, etc) |
| `refactor` | Refactorización gruesa o estructuración que no afecta a la funcionalidad final |
| `test` | Arreglo de cobertura, carga de nuevos scripts de *testing* unitario |
| `chore` | Actualización de dependencias o tareas de aburrimiento técnico general |
| `perf` | Refactor enfocado estrictamente en mejorar métricas de rendimiento |
| `ci` | Ajustes de CI/CD, configuración de despliegue, *pipelines* |

### Ejemplo del resultado de la IA

```text
feat(docs): add comprehensive Source Control documentation
- Create new documentation page for Source Control features
- Update interface documentation to link to Source Control page
- Provide detailed explanation of AI-powered commit message generation
- Describe diff context provider and commit message generation process
```

---

## Proveedor de contexto Git Diff

Kiro incluye espectacularmente el proveedor de contexto `#Git Diff`. Su gracia es permitirte arrobar todos los "cambios vivos sin guardar" directamente en tu mensaje de chat. Esto es brillante para:

- Solucionar conflictos dolorosos de repositorios mergeados.
- Pedirle a la IA que revise *Code Review* estricto de los cambios antes de tirarlos a producción mediante *commit*.
- Dejar que lea por qué se te rompió algo analizando la diferencia entre la rama `main` y tu desastre en el teclado.

### Ejemplo de uso

```text
Che Kiro, ¿me ayudás arreglando los merge conflicts de este archivo? #Git Diff
```

---

## Resolución de problemas

### Falla en operaciones directas de Git

- Revisá dos veces tu configuración global de Git o certificados.
- Comprobá que de verdad tengas permisos de GitHub/GitLab autorizados para ese repositorio al pushear.