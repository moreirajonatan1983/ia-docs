# Ejemplos de hooks

> **Fuente:** [kiro.dev/docs/hooks/examples/](https://kiro.dev/docs/hooks/examples/)

---

Ejemplos prácticos y plantillas listas para usar en tus proyectos.

---

## Escáner de commit previa de seguridad

Previene fugas de seguridad escaneando archivos antes de ser comprometidos.

| Campo | Valor |
|---|---|
| **Disparador** | Parada del agente |
| **Acción** | Aviso del agente |

**Aviso:**
```
Revise los archivos modificados para detectar posibles problemas de seguridad:
1. Busque claves, tokens o credenciales de API en el código fuente
2. Verifique claves privadas o credenciales confidenciales
3. Busque claves o certificados de cifrado
4. Identificar tokens de autenticación o ID de sesión
5. Marcar contraseñas o secretos en archivos de configuración
6. Detectar direcciones IP que contengan datos confidenciales
7. Encuentre URL internas codificadas
8. Detectar las credenciales de conexión a la base de datos

Para cada problema encontrado:
1. Resalte el riesgo de seguridad específico
2. Sugerir un enfoque alternativo seguro
3. Recomendar mejores prácticas de seguridad
```

---

## Registro centralizado de mensajes de usuario

Loguea todos los avisos de usuario a un sistema centralizado para análisis y auditoría.

| Campo | Valor |
|---|---|
| **Disparador** | Envío rápido |
| **Acción** | Comando Shell |

**Comando:**
```golpecito
# Registrar mensaje de usuario en Grafana Loki
curl -H "Tipo de contenido: aplicación/json" -XPOST \
  "http://loghost/loki/api/v1/push" --data-raw\
  "{'streams': [{ 'stream': { 'app': 'kiro', 'user': \"${USER}\" }, 'values': [ [\"$(date +%s%N)\", \"${USER_PROMPT}\"] ] }]}"
```

---

## Ayudante de Internacionalización

Mantiene las traducciones sincronizadas cuando se actualiza el archivo del idioma principal.

| Campo | Valor |
|---|---|
| **Disparador** | Guardar archivo |
| **Objetivo** | `src/locales/en/*.json` |
| **Acción** | Aviso del agente |

**Aviso:**
```
Cuando se actualiza un archivo local en inglés:
1. Identifique qué claves de cadena se agregaron o modificaron
2. Verifique todos los archivos de otros idiomas para estas claves.
3. Si faltan claves, agréguelas con un marcador "NEEDS_TRANSLATION".
4. Para claves modificadas, márquelas como "NEEDS_REVIEW"
5. Genere un resumen de los cambios necesarios en todos los idiomas.
```

---

## Mantenedor de cobertura de prueba

Asegúrese de que la cobertura de pruebas se mantenga alta a medida que el código evolucione.

| Campo | Valor |
|---|---|
| **Disparador** | Guardar archivo |
| **Objetivo** | `src/**/*.{js,ts,jsx,tsx}` |
| **Acción** | Aviso del agente |

**Aviso:**
```
Cuando se modifica un archivo fuente:
1. Identificar funciones y métodos nuevos o modificados.
2. Verificar si existen pruebas correspondientes y cubrir los cambios.
3. Si falta cobertura, genere casos de prueba para el nuevo código.
4. Ejecute las pruebas para verificar que pasen.
5. Actualizar informes de cobertura
```

---

## Generador de documentación

Genera documentación completa bajo demanda para el archivo actual.

| Campo | Valor |
|---|---|
| **Disparador** | manuales |
| **Acción** | Aviso del agente |

**Aviso:**
```
Genere documentación completa para el archivo actual:
1. Extraer firmas de funciones y clases
2. Parámetros del documento y tipos de devolución.
3. Proporcionar ejemplos de uso basados en el código existente.
4. Actualice README.md con cualquier exportación nueva.
5. Asegúrese de que la documentación siga los estándares del proyecto.
```

---

## Integración con MCP

Los hooks pueden potenciarse con MCP para acceder a herramientas externas especializadas.

**Cómo usar MCP con hooks:**
1. [Configurar servidores MCP →](../13_MCP/01_Configuration.md)
2. Referenciar las herramientas MCP en las instrucciones del hook
3. Configurar `autoApprove` para herramientas de uso frecuente

**Casos de uso:**
- Verifica que tu sistema de diseño Figma sea respetado
- Actualizar el estado de un ticket después de completar una tarea
- Sincronizar una base de datos desde archivos del proyecto