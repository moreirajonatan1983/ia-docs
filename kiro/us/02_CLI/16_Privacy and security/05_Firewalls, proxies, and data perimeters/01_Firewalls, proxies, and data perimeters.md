# Firewalls, Proxies, and Data Perimeters

> **Source:** [kiro.dev/docs/cli/privacy-and-security/firewalls-proxies/](https://kiro.dev/docs/cli/privacy-and-security/firewalls-proxies/)

---

## Overview

Si tu organización usa firewalls, proxies corporativos o data perimeters, necesitás configurarlos para permitir el tráfico de Kiro CLI.

---

## Required Endpoints

Permitir el acceso a los siguientes dominios:

| Dominio | Puerto | Propósito |
|---|---|---|
| `*.kiro.dev` | 443 (HTTPS) | API principal y autenticación |
| `*.amazonaws.com` | 443 (HTTPS) | Servicios AWS backend |
| `*.awsapps.com` | 443 (HTTPS) | IAM Identity Center (Enterprise) |

---

## HTTP/HTTPS Proxy Configuration

Kiro CLI respeta las variables de entorno estándar de proxy:

```bash
# Proxy HTTP
export HTTP_PROXY=http://proxy.company.com:8080
export HTTPS_PROXY=http://proxy.company.com:8080

# Excluir dominios del proxy
export NO_PROXY=localhost,127.0.0.1,.company.internal

# Variantes en minúsculas (también soportadas)
export http_proxy=http://proxy.company.com:8080
export https_proxy=http://proxy.company.com:8080
```

---

## SSL/TLS Certificate Inspection

Si tu organización usa inspección de SSL/TLS (man-in-the-middle), podés necesitar:

1. Agregar el certificado root de tu proxy al store de certificados del sistema
2. O configurar la variable de entorno:
```bash
export SSL_CERT_FILE=/path/to/corporate-ca.pem
export NODE_EXTRA_CA_CERTS=/path/to/corporate-ca.pem
```

---

## Data Perimeters (Enterprise)

Para organizaciones que requieren que todo el tráfico permanezca dentro de la red de AWS, Kiro soporta **VPC Endpoints (AWS PrivateLink)**.

Ver [VPC Endpoints →](./06_VPC endpoints (AWS PrivateLink).md) para configuración detallada.

---

## Troubleshooting Connectivity

```bash
# Verificar que podés acceder a la API de Kiro
curl -v https://api.kiro.dev/health

# Verificar con proxy explícito
curl -v --proxy http://proxy.company.com:8080 https://api.kiro.dev/health

# Diagnóstico completo
kiro-cli doctor --all
```

---

## Common Firewall Rules

```
# Regla de ejemplo para firewall corporativo (IPv4)
ALLOW TCP 443 -> *.kiro.dev
ALLOW TCP 443 -> *.amazonaws.com
ALLOW TCP 443 -> *.awsapps.com     # Solo Enterprise
```