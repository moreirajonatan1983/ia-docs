# Security Considerations

> **Source:** [kiro.dev/docs/cli/chat/security/](https://kiro.dev/docs/cli/chat/security/)

---

## Understanding Security Risks

Al usar Kiro, tené en cuenta los siguientes riesgos potenciales:

| Riesgo | Ejemplo |
|---|---|
| **Cambios no deseados al sistema** | Kiro puede interpretar requests de forma inesperada |
| **Modificaciones a recursos AWS** | Recursos pueden crearse, modificarse o eliminarse, afectando entornos productivos o generando costos |
| **Pérdida de datos** | Comandos que eliminan o sobreescriben archivos |
| **Vulnerabilidades de seguridad** | Comandos que comprometen la seguridad del sistema |

Estos riesgos se incrementan significativamente al usar `/tools trust-all` o `/acceptall`, que bypasean las confirmaciones.

**Ejemplos concretos:**
- `"clean up old files"` → puede eliminar archivos de configuración importantes
- `"optimize my EC2 instances"` → puede terminar instancias en ejecución
- `"fix security issues"` → puede modificar permisos exponiendo datos sensibles

> ⚠️ **No uses `/tools trust-all` o `/acceptall` en entornos productivos o con datos sensibles. Sos responsable de todas las acciones ejecutadas por Kiro.**

---

## General Security Best Practices

### Restricting File Access

Por defecto, Kiro puede leer archivos sin pedir permiso (Read es trusted por defecto). Para entornos sensibles, podés restringir esto:

```bash
/tools untrust read
```

Con esta configuración, Kiro pedirá permiso explícito antes de leer cualquier archivo.

Para hacerlo persistente, agregá a tu shell startup script:
```bash
echo 'alias kiro-cli="kiro-cli --untrust-fs-read"' >> ~/.bashrc
```

### Additional Security Measures

Para entornos con información altamente sensible:

- Usá Kiro en un entorno de desarrollo dedicado que **no contenga** credenciales sensibles o datos privados
- Almacená archivos sensibles fuera de tus directorios de proyecto o en ubicaciones con permisos restringidos
- Usá variables de entorno para valores sensibles en lugar de hardcodearlos en archivos
- Considerá usar `/tools untrust aws` para requerir permiso explícito antes de hacer llamadas a la API de AWS
- Usá Steering para definir pautas y restricciones de seguridad

### Using `/tools trust-all` Safely

Si tenés que usar `/tools trust-all` o `/acceptall` para workflows específicos:

| Práctica | Descripción |
|---|---|
| Solo en dev/testing | **Nunca** en producción |
| Scope temporal | Habilitá solo para tareas específicas → deshabilitet con `/tools reset` |
| Backup previo | Realizá backup de datos importantes antes de habilitarlo |
| Permisos mínimos | Usá credenciales AWS con permisos mínimos |
| Monitoreo activo | Monitoreá todas las acciones de Kiro mientras está habilitado |

Para volver a los permisos por defecto:
```bash
/tools reset
```

Esto revierte todas las herramientas a sus niveles de permiso por defecto (solo Read trusted).

---

## Related

- [Permissions →](./09_Permissions.md)
- [Configuration →](./13_Configuration.md)
- [Data Protection →](../../01_IDE/15_Privacy%20and%20security/01_Data%20protection.md)