# Working with Images

> **Source:** [kiro.dev/docs/cli/chat/images/](https://kiro.dev/docs/cli/chat/images/)

---

Kiro can analyze and discuss images directly in your chat session.

---

## Methods to Share Images

### 1. Drag and Drop

Drag an image directly into your terminal window:
1. The image path is automatically inserted into your prompt
2. Add text to provide context
3. Kiro processes and responds based on the image content

```
Kiro> /path/to/architecture-diagram.png Can you explain this architecture and generate sample code?
```

### 2. Using the `read` Tool

Explicitly reference image files:

```
Kiro> Can you analyze this screenshot at /path/to/screenshot.png?
```

Kiro automatically suggests using `fs_read` with Image mode when you mention image files.

### 3. Paste from Clipboard

Paste an image from your system clipboard:

```
/paste
```

---

## Image Use Cases

- Analyzing screenshots of error messages for troubleshooting
- Converting architecture diagrams into code implementations
- Discussing UI/UX designs and generating corresponding HTML/CSS
- Understanding flowcharts and translating them into algorithms
- Reviewing code snippets shared as images
- Interpreting technical diagrams for documentation

---

## Supported Formats and Limitations

| Property | Value |
|---|---|
| **Formats** | JPEG/JPG, PNG, GIF, WebP |
| **Max size** | 10MB per image |
| **Max images per request** | 10 |

**Best practices:**
- Use high-resolution images with clear text
- Provide specific instructions about what you want Kiro to do
- For complex diagrams, provide additional context