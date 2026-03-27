# Trabajar con imágenes

> **Fuente:** [kiro.dev/docs/cli/chat/images/](https://kiro.dev/docs/cli/chat/images/)

---

Kiro puede analizar y discutir imágenes directamente en su sesión de chat.

---

## Métodos para compartir imágenes

### 1. Arrastrar y soltar

Arrastre una imagen directamente a la ventana de su terminal:
1. La ruta de la imagen se inserta automáticamente en su mensaje.
2. Agregue texto para proporcionar contexto.
3. Kiro procesa y responde según el contenido de la imagen.

```
Kiro> /path/to/architecture-diagram.png Can you explain this architecture and generate sample code?
```

### 2. Usando la herramienta `leer`

Archivos de imagen de referencia explícita:

```
Kiro> Can you analyze this screenshot at /path/to/screenshot.png?
```

Kiro sugiere automáticamente usar `fs_read` con el modo Imagen cuando mencionas archivos de imagen.

### 3. Pegar desde el portapapeles

Pegue una imagen del portapapeles de su sistema:

```
/paste
```

---

## Casos de uso de imágenes

- Análisis de capturas de pantalla de mensajes de error para solucionar problemas.
- Convertir diagramas de arquitectura en implementaciones de código.
- Discutir diseños UI/UX y generar HTML/CSS correspondiente.
- Comprender diagramas de flujo y traducirlos en algoritmos.
- Revisar fragmentos de código compartidos como imágenes.
- Interpretación de esquemas técnicos para documentación.

---

## Formatos admitidos y limitaciones

| Propiedad | Valor |
|---|---|
| **Formatos** | JPEG/JPG, PNG, GIF, WebP |
| **Tamaño máximo** | 10 MB por imagen |
| **Máximo de imágenes por solicitud** | 10 |

**Mejores prácticas:**
- Utilice imágenes de alta resolución con texto claro
- Proporciona instrucciones específicas sobre lo que quieres que haga Kiro.
- Para diagramas complejos, proporcione contexto adicional