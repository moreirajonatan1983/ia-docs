# Custom Extension Registry

> **Source:** [kiro.dev/docs/editor/extension-registry/](https://kiro.dev/docs/editor/extension-registry/)

---

Kiro supports using a custom extension registry instead of the default [Open VSX Registry](https://open-vsx.org). This is useful for organizations that host their own private extension marketplace.

---

## Configuring a Different Extension Marketplace

### Step 1 — Locate the `product.json` file

Find the file on disk. The exact location depends on the platform:

| Platform | Path |
|---|---|
| **macOS** | `/Applications/Kiro.app/Contents/Resources/app/product.json` |
| **Windows** | `C:\Program Files\Kiro\resources\app\product.json` |
| **Linux** | `/usr/lib/code/product.json` |

### Step 2 — Edit the `extensionsGallery` property

Open `product.json` in an editor and locate the `extensionsGallery` property. Update `serviceUrl`, `itemUrl`, and `resourceUrlTemplate` to point to your private registry instead of `https://open-vsx.org`.

### Step 3 — Apply the configuration

For example, if your custom registry is hosted at `https://registry.example.com`, update the `extensionsGallery` property as follows:

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

## Enterprise Deployment

To configure all Kiro installs in your organization to use a custom extension registry, use an endpoint management, **Mobile Device Management (MDM)** solution, or similar to make the above update to `product.json` across all your devices.