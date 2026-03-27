# Web Tools

![Webtools](https://kiro.dev/videos/webtools.mp4)


> **Source:** [kiro.dev/docs/chat/webtools/](https://kiro.dev/docs/chat/webtools/)

---

Las web tools permiten a Kiro obtener contenido de la web y enriquecer sus respuestas con resultados de búsqueda web.

---

## Overview

Con las web tools, Kiro puede:

- **Fetch content** — Obtener el contenido de una URL específica para usarlo como contexto
- **Web search** — Fundamentar respuestas con resultados de búsqueda actuales

Para usar el fetch: pegá una URL en el chat y Kiro la procesará como contexto.

---

## Limitations

| Parámetro | Límite |
|---|---|
| **Tamaño máximo por página** | 10 MB |
| **Timeout por request** | 30 segundos |
| **Redirects máximos** | 10 |
| **Tipo de contenido** | Solo páginas `text/html` |
| **Reintentos automáticos** | 3 intentos en caso de falla |

---

## Governance

Los clientes del tier **Pro que usan IAM Identity Center** como método de inicio de sesión pueden controlar el acceso a las web tools para los usuarios de su organización.

- Web tools están **habilitadas por defecto** en Kiro
- Los administradores pueden deshabilitarlas desde la consola de AWS
- ⚠️ La restricción se aplica en el lado del cliente — los usuarios finales podrían evitarla

---

## Disabling Web Tools for Your Organization

1. Ir a la consola de AWS
2. Navegar a la configuración de Amazon Q / Kiro para tu organización
3. Deshabilitar web tools para los usuarios del tenant

---

## Related

- [Privacy and Security →](../11_Privacy and security.md)
- [Powers →](../09_Powers.md) — Alternativa para acceder a documentación especializada sin web search