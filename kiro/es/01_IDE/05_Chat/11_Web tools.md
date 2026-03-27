# Herramientas web

![Herramientas web](https://kiro.dev/videos/webtools.mp4)

> **Fuente:** [kiro.dev/docs/chat/webtools/](https://kiro.dev/docs/chat/webtools/)

---

Las herramientas web permiten a Kiro obtener contenido de la web y enriquecer sus respuestas con resultados de búsqueda web.

---

## Descripción general

Con las herramientas web, Kiro puede:

- **Obtener contenido** — Obtener el contenido de una URL específica para usar como contexto
- **Búsqueda web** — Fundamentar respuestas con resultados de búsqueda actuales

Para usar el fetch: pegá una URL en el chat y Kiro la procesará como contexto.

---

## Limitaciones

| Parámetro | Límite |
|---|---|
| **Tamaño máximo por página** | 10MB |
| **Tiempo de espera por solicitud** | 30 segundos |
| **Redirecciones máximas** | 10 |
| **Tipo de contenido** | Solo páginas `text/html` |
| **Reintentos automáticos** | 3 intentos en caso de falla |

---

## Gobernanza

Los clientes del nivel **Pro que usan IAM Identity Center** como método de inicio de sesión pueden controlar el acceso a las herramientas web para los usuarios de su organización.

- Herramientas web están **habilitadas por defecto** en Kiro
- Los administradores pueden deshabilitarlas desde la consola de AWS
- ⚠️ La restricción se aplica en el lado del cliente — los usuarios finales podrían evitarla

---

## Deshabilitar las herramientas web para su organización

1. Ir a la consola de AWS
2. Navegar a la configuración de Amazon Q / Kiro para tu organización
3. Deshabilitar herramientas web para los usuarios del inquilino

---

## Relacionado

- [Privacidad y Seguridad →](../11_Privacidad y seguridad.md)
- [Powers →](../09_Powers.md) — Alternativa para acceder a documentación especializada sin búsqueda web