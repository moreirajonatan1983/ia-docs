# Referencias de archivos

> **Fuente:** [kiro.dev/docs/cli/chat/file-references/](https://kiro.dev/docs/cli/chat/file-references/)

---

Incluya contenidos de archivos o listados de directorios en línea en sus mensajes usando la sintaxis `@path`.

---

## Uso básico

Escriba `@` seguido de una ruta de archivo o directorio:

```
@src/index.ts          # Include file contents
@src/                  # Include directory tree
@./relative/path       # Relative paths
@"path with spaces.txt" # Quoted paths (required for spaces)
```

Las referencias pueden aparecer en cualquier parte de su mensaje:

```
Review @src/auth.ts for security issues
Compare @old.json with @new.json
What's in @src/ that handles authentication?
```

---

## Completar pestaña

Presione `Tab` después de `@` para completar automáticamente las rutas:

```
@src/<Tab>           # Shows files in src/
@package<Tab>        # Completes to @package.json
@"Screenshot 2024<Tab>   # Completes to @"Screenshot 2024-01.png"
```

La finalización funciona en cualquier parte de la línea de entrada. Las comillas se agregan automáticamente para los caminos con espacios.

---

## Cómo se resuelven las referencias

Cuando una referencia puede coincidir tanto con un mensaje como con un archivo:
1. **Preguntas primero**: si `@nombre` coincide con una petición de `/lista de peticiones`, se trata como una petición
2. **Archivos segundo**: de lo contrario, se marca como ruta de archivo
3. **Directorios terceros**: si no es un archivo, se marca como directorio

Forzar resolución de archivos: `@./myfile`

---

## Manejo de archivos

- **Compatible:** Archivos de texto (código fuente, configuración, rebajas) de hasta **250 KB**
- **No compatible:** Archivos binarios (imágenes, ejecutables, archivos): muestra un error
- **Archivos grandes:** Truncado a 250 KB con una advertencia: `⚠ El archivo 'large-file.json' fue truncado`

---

## Árboles de directorios

`@src/` se expande a una lista de árbol:

```
src/
├── lib/
│   ├── auth.ts
│   └── utils.ts
├── index.ts
└── config.json
```

**Límites:**
- Profundidad máxima: 3 niveles
- Máximo de elementos por nivel: 10 (muestra "... (N más elementos)" si se excede)
- Ignora: `node_modules`, `.git`, `target`, `dist`, `build`

---

## Ejemplos

```
> Review @src/auth.ts for security issues
> What's different between @v1/handler.py and @v2/handler.py?
> What's the structure of @infra/cdk/?
> Using the config in @serverless.yml, update @src/lambda/index.ts
```

---

## Limitaciones actuales

- Archivos de texto de hasta 250 KB únicamente (los archivos más grandes se truncan)
- Árboles de directorios de hasta 3 niveles de profundidad, 10 elementos por nivel
- Solo rutas explícitas: no hay patrones globales como `@*.ts`
- Solo el contenido completo del archivo: no hay rangos de líneas como `@file.ts:10-20`
- Sin expansión de tilde como `@~/file`
- Los archivos binarios no son compatibles