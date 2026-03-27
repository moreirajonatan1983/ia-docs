# Consideraciones de seguridad

> **Fuente:** [kiro.dev/docs/cli/chat/security/](https://kiro.dev/docs/cli/chat/security/)

---

## Comprender los riesgos de seguridad

Al usar Kiro, tuvo en cuenta los siguientes riesgos potenciales:

| Riesgo | Ejemplo |
|---|---|
| **Cambios no deseados al sistema** | Kiro puede interpretar solicitudes de forma inesperada |
| **Modificaciones a recursos AWS** | Recursos pueden crearse, modificarse o eliminarse, afectando entornos productivos o generando costos |
| **Pérdida de datos** | Comandos que eliminan o sobreescriben archivos |
| **Vulnerabilidades de seguridad** | Comandos que comprometen la seguridad del sistema |

Estos riesgos se incrementan significativamente al usar `/tools trust-all` o `/acceptall`, que pasan por alto las commits.

**Ejemplos concretos:**
- `"limpiar archivos antiguos"` → puede eliminar archivos de configuración importantes
- `"optimizar mis instancias EC2"` → puede terminar instancias en ejecución
- `"solucionar problemas de seguridad"` → puede modificar permisos exponiendo datos sensibles

> ⚠️ **No uses `/tools trust-all` o `/acceptall` en entornos productivos o con datos sensibles. Sos responsable de todas las acciones ejecutadas por Kiro.**

---

## Mejores prácticas generales de seguridad

### Restringir el acceso a archivos

Por defecto, Kiro puede leer archivos sin pedir permiso. Para entornos sensibles, podría restringir esto:

```bash
/tools untrust read
```

Con esta configuración, Kiro pedirá permiso explícito antes de leer cualquier archivo.

Para hacerlo persistente, agregue a su script de inicio de shell:
```golpecito
echo 'alias kiro-cli="kiro-cli --untrust-fs-read"' >> ~/.bashrc
```

### Medidas de seguridad adicionales

Para entornos con información altamente sensible:

- Usá Kiro en un entorno de desarrollo dedicado que **no contiene** credenciales sensibles o datos privados
- Almacená archivos sensibles fuera de tus directorios de proyecto o en ubicaciones con permisos restringidos
- Usamos variables de entorno para valores sensibles en lugar de codificarlos en archivos
- Considerá usar `/tools untrust aws` para requerir permiso explícito antes de hacer llamadas a la API de AWS
- Usá Steering para definir pautas y restricciones de seguridad

### Usando `/tools trust-all` de forma segura

Si tienes que usar `/tools trust-all` o `/acceptall` para flujos de trabajo específicos:

| Práctica | Descripción |
|---|---|
| Solo en desarrollo/pruebas | **Nunca** en producción |
| Alcance temporal | Habilitá solo para tareas específicas → deshabilitat con `/tools reset` |
| Copia de seguridad anterior | Realice una copia de seguridad de datos importantes antes de habilitarlo |
| Permisos mínimos | Usa credenciales AWS con permisos mínimos |
| Monitoreo activo | Monitoreá todas las acciones de Kiro mientras está habilitado |

Para volver a los permisos por defecto:
```golpecito
/restablecer herramientas
```

Esto revierte todas las herramientas a sus niveles de permiso por defecto (solo Readtrusted).

---

## Relacionado

- [Permisos →](./09_Permissions.md)
- [Configuración →](./13_Configuration.md)
- [Protección de datos →](../../01_IDE/15_Privacy%20and%20security/01_Data%20protection.md)