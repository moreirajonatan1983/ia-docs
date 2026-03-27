# Herramientas de diferenciación personalizadas

> **Fuente:** [kiro.dev/docs/cli/chat/diff-tools/](https://kiro.dev/docs/cli/chat/diff-tools/)

---

Podrá configurar herramientas de diferencias externas para visualizar los cambios de código propuestos por Kiro CLI.

---

## Configuración

Configura tu herramienta de diferenciación preferida con la configuración `chat.diffTool`:

```golpecito
# Configurar una herramienta
configuración de kiro-cli chat.diffTool delta

# Con argumentos personalizados
configuración de kiro-cli chat.diffTool "delta --side-by-side"

# Restablecer el diferencial integrado
configuración de kiro-cli -d chat.diffTool
```

---

## Herramientas terminales

Muestran diferencias directamente en la terminal — mantienen el flujo de trabajo:

| Herramienta | comando |
|---|---|
| [delta](https://github.com/dandavison/delta) | `delta` |
| [difftastic](https://github.com/Wilfred/difftastic) | `diferente` |
| [icdiff](https://github.com/jeffkaufman/icdiff) | `icdiff` |
| [diff-so-fancy](https://github.com/so-fancy/diff-so-fancy) | `diferente-tan-elegante` |
| [colordiff](https://www.colordiff.org/) | `colordiff` |
| [ydiff](https://github.com/ymattw/ydiff) | `ydiff` |
| [murciélago](https://github.com/sharkdp/bat) | `murciélago` |

---

## Herramientas GUI

Abra una ventana separada para revisar cambios:

| Herramienta | comando |
|---|---|
| Código VS | `código` |
| VSCodio | `codio` |
| Merge | `merge` |
| KDiff3 | `kdiff3` |
| Combinación de archivos (macOS) | `opendiff` |
| Vim | `vimdiff`/`vim`/`nvim` |

> ⚠️ Las herramientas GUI abren archivos temporales solo para visualización. Las ediciones que hagas en la GUI **no se guardan ni aplican** a los cambios propuestos por Kiro.

---

## Argumentos personalizados

Podés personalizar el comportamiento incluyendo argumentos entre comillas:

```bash
# Side-by-side view con delta
kiro-cli settings chat.diffTool "delta --side-by-side"
```

---

## Otras herramientas

Kiro puede trabajar con herramientas no listadas. Cuando configuras una herramienta, Kiro intenta dos enfoques:
1. Envía un unified diff a la herramienta vía stdin
2. Invoca la herramienta con dos rutas de archivos temporales como argumentos

Si ningún enfoque funciona, Kiro vuelve al diff inline integrado.

---

## Solución de problemas

Si ves el error `"No se pudo encontrar la herramienta de diferenciación"`, la herramienta no está instalada o no está en tu RUTA:

```golpecito
# Verificar que está en el PATH
cual delta

# Delta instalador
#macOS
instalar cerveza git-delta

#Ubuntu/Debian
sudo apto instalar git-delta
```

Consulte la documentación de la herramienta específica para instrucciones de instalación.