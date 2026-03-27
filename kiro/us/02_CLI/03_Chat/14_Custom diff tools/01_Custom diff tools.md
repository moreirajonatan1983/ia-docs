# Custom Diff Tools

> **Source:** [kiro.dev/docs/cli/chat/diff-tools/](https://kiro.dev/docs/cli/chat/diff-tools/)

---

Podés configurar herramientas de diff externas para visualizar los cambios de código propuestos por Kiro CLI.

---

## Configuration

Configurá tu herramienta de diff preferida con el setting `chat.diffTool`:

```bash
# Configurar una herramienta
kiro-cli settings chat.diffTool delta

# Con argumentos personalizados
kiro-cli settings chat.diffTool "delta --side-by-side"

# Resetear al diff integrado
kiro-cli settings -d chat.diffTool
```

---

## Terminal Tools

Muestran diffs directamente en la terminal — mantienen el flujo de trabajo:

| Tool | Comando |
|---|---|
| [delta](https://github.com/dandavison/delta) | `delta` |
| [difftastic](https://github.com/Wilfred/difftastic) | `difft` |
| [icdiff](https://github.com/jeffkaufman/icdiff) | `icdiff` |
| [diff-so-fancy](https://github.com/so-fancy/diff-so-fancy) | `diff-so-fancy` |
| [colordiff](https://www.colordiff.org/) | `colordiff` |
| [ydiff](https://github.com/ymattw/ydiff) | `ydiff` |
| [bat](https://github.com/sharkdp/bat) | `bat` |

---

## GUI Tools

Abren una ventana separada para revisar cambios:

| Tool | Comando |
|---|---|
| VS Code | `code` |
| VSCodium | `codium` |
| Meld | `meld` |
| KDiff3 | `kdiff3` |
| FileMerge (macOS) | `opendiff` |
| Vim | `vimdiff` / `vim` / `nvim` |

> ⚠️ Las GUI tools abren archivos temporales solo para visualización. Los edits que hagas en la GUI **no se guardan ni aplican** a los cambios propuestos por Kiro.

---

## Custom Arguments

Podés personalizar el comportamiento incluyendo argumentos entre comillas:

```bash
# Side-by-side view con delta
kiro-cli settings chat.diffTool "delta --side-by-side"
```

---

## Other Tools

Kiro puede trabajar con herramientas no listadas. Cuando configurás una herramienta, Kiro intenta dos enfoques:
1. Envía un unified diff a la herramienta vía stdin
2. Invoca la herramienta con dos rutas de archivos temporales como argumentos

Si ningún enfoque funciona, Kiro vuelve al diff inline integrado.

---

## Troubleshooting

Si ves el error `"Couldn't find the diff tool"`, la herramienta no está instalada o no está en tu PATH:

```bash
# Verificar que está en el PATH
which delta

# Instalar delta
# macOS
brew install git-delta

# Ubuntu/Debian
sudo apt install git-delta
```

Consultá la documentación de la herramienta específica para instrucciones de instalación.