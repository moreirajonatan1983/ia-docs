# Firewalls, proxies y perímetros de datos

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/firewalls-proxies/](https://kiro.dev/docs/cli/privacy-and-security/firewalls-proxies/)

---

## Descripción general

Si tu organización utiliza firewalls, proxies corporativos o perímetros de datos, necesitarás configurarlos para permitir el tráfico de Kiro CLI.

---

## endpoints requeridos

Permitir el acceso a los siguientes dominios:

| Dominio | Puerto | Propósito |
|---|---|---|
| `*.kiro.dev` | 443 (HTTPS) | API principal y autenticación |
| `*.amazonaws.com` | 443 (HTTPS) | Servicios backend de AWS |
| `*.awsapps.com` | 443 (HTTPS) | Centro de Identidad IAM (Empresa) |

---

## Configuración del proxy HTTP/HTTPS

Kiro CLI respeta las variables de entorno estándar de proxy:

```golpecito
# Proxy HTTP
exportar HTTP_PROXY=http://proxy.company.com:8080
exportar HTTPS_PROXY=http://proxy.company.com:8080

# Excluir dominios del proxy
exportar NO_PROXY=localhost,127.0.0.1,.empresa.internal

# Variantes en minúsculas (también soportadas)
exportar http_proxy=http://proxy.company.com:8080
exportar https_proxy=http://proxy.company.com:8080
```

---

## Inspección de certificados SSL/TLS

Si tu organización usa inspección de SSL/TLS (man-in-the-middle), podrías necesitar:

1. Agregar el certificado root de tu proxy al store de certificados del sistema
2. O configurar la variable de entorno:
```golpecito
exportar SSL_CERT_FILE=/ruta/a/corporate-ca.pem
exportar NODE_EXTRA_CA_CERTS=/ruta/a/corporate-ca.pem
```

---

## Perímetros de datos (empresarial)

Para organizaciones que requieren que todo el tráfico permanezca dentro de la red de AWS, Kiro soporta **VPC Endpoints (AWS PrivateLink)**.

Consulte [endpoints de VPC →](./06_Puntos finales de VPC (AWS PrivateLink).md) para configurar detalladamente.

---

## Solución de problemas de conectividad

```golpecito
# Verificar que podés acceder a la API de Kiro
rizo -v https://api.kiro.dev/health

# Verificar con proxy explícito
curl -v --proxy http://proxy.company.com:8080 https://api.kiro.dev/health

# Diagnóstico completo
kiro-cli doctor --todos
```

---

## Reglas comunes de firewall

```
# Regla de ejemplo para firewall corporativo (IPv4)
ALLOW TCP 443 -> *.kiro.dev
ALLOW TCP 443 -> *.amazonaws.com
ALLOW TCP 443 -> *.awsapps.com     # Solo Enterprise
```