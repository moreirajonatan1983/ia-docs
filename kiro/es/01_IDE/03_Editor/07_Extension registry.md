# Registro de extensión personalizado (Extension registry)

> **Fuente:** [kiro.dev/docs/editor/extension-registry/](https://kiro.dev/docs/editor/extension-registry/)

---

Kiro tiene soporte para inyectar su base leyendo los plugins desde un *Extension registry* 100% personalizado mediante túnel, saltándose completamente el registro oficial que viene clavado por defecto de [Open VSX Registry](https://open-vsx.org). Esto le soluciona literal la vida a corporaciones de alto calibre que obligatoriamente deben atornillar su propio marketplace en servidores on-premise privados aislados del público general.

---

## Configurar un supermercado centralizado (Marketplace privado)

### Paso 1: Localizá el eslabón maestro `product.json`

Vas a tener que encontrar el santo grial en tu disco de máquina. Obvio, la vida de esta variable dependerá estrictamente del sistema operativo que tengas vivo:

| Sistema Operativo | Directorio de archivo duro |
|---|---|
| **macOS** | `/Applications/Kiro.app/Contents/Resources/app/product.json` |
| **Windows** | `C:\Program Files\Kiro\resources\app\product.json` |
| **Linux** | `/usr/lib/code/product.json` |

### Paso 2: Edita la constante intocable `extensionsGallery`

Agarrá tu sublime/nano/bloc o cualquiera de uso y buscá explícitamente el objeto core indexado llamado `extensionsGallery`.
Meté la cuchara ahí actualizando sus variables internas de las propiedades primarias `serviceUrl`, `itemUrl`, y el grandioso `resourceUrlTemplate` apuntando hacia el subdominio HTTP/HTTPS de tu propio servidor corporativo en rotundo detrimento del original `https://open-vsx.org`.

### Paso 3: Aplicar este conocimiento destructivo/creativo

Miralo con tus propios ojos: si a tu empresa corporativa se le ocurrió armar el servidor montado en una URL llamada `https://registry.example.com`, el objeto `extensionsGallery` a reventar dentro de tu disco tiene que terminar viéndose quirúrgicamente así:

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

## Moviéndolo a toda la oficina (Implementación Enterprise)

Para dominar en cadena y estandarizar forzosamente sin ir bajando de computadora en computadora de la oficina de desarrollo a forzar la escritura oculta del archivo `product.json`, hacela corta y aplicá reglas duras mediante políticas locales (Endpoint administration / GPOs), soluciones de infraestructura y aprovisionamientos de máquinas unificadas (**Mobile Device Management - MDM**) para masacrar silenciosamente dichos JSON mediante scripts bash en toda la red corporativa de programadores autorizados.