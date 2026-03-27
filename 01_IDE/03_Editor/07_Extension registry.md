# Registro de extensión personalizado

> **Fuente:** [kiro.dev/docs/editor/extension-registry/](https://kiro.dev/docs/editor/extension-registry/)

---

Kiro admite el uso de un registro de extensión personalizado en lugar del [Registro Open VSX] predeterminado (https://open-vsx.org). Esto es útil para organizaciones que albergan su propio mercado de extensión privado.

---

## Configurar un mercado de extensiones diferente

### Paso 1: busque el archivo `product.json`

Busque el archivo en el disco. La ubicación exacta depende de la plataforma:

| Plataforma | Camino |
|---|---|
| **macOS** | `/Aplicaciones/Kiro.app/Contents/Resources/app/product.json` |
| **Windows** | `C:\Archivos de programa\Kiro\resources\app\product.json` |
| **Linux** | `/usr/lib/code/product.json` |

### Paso 2: edite la propiedad `extensionsGallery`

Abra `product.json` en un editor y busque la propiedad `extensionsGallery`. Actualice `serviceUrl`, `itemUrl` y `resourceUrlTemplate` para que apunten a su registro privado en lugar de `https://open-vsx.org`.

### Paso 3: aplicar la configuración

Por ejemplo, si su registro personalizado está alojado en `https://registry.example.com`, actualice la propiedad `extensionsGallery` de la siguiente manera:

```json
"extensionsGallery": {
    "serviceUrl": "https://registry.example.com/vscode/gallery",
    "itemUrl": "https://registry.example.com/vscode/item",
    "resourceUrlTemplate": "https://registry.example.com/vscode/unpkg/{publisher}/{name}/{version}/{path}",
    "controlUrl": "",
    "recommendationsUrl": "",
    "nlsBaseUrl": "",
    "publisherUrl": ""
}
```

---

## Implementación empresarial

Para configurar todas las instalaciones de Kiro en su organización para usar un registro de extensión personalizado, use una solución de administración de puntos finales, **Administración de dispositivos móviles (MDM)** o similar para realizar la actualización anterior a `product.json` en todos sus dispositivos.