# VPC Endpoints (AWS PrivateLink)

> **Source:** [kiro.dev/docs/cli/privacy-and-security/vpc-endpoints/](https://kiro.dev/docs/cli/privacy-and-security/vpc-endpoints/)

---

## Overview

**AWS PrivateLink** permite que Kiro CLI se comunique con los servicios de AWS sin que el tráfico salga a Internet público. Ideal para organizaciones con requisitos estrictos de seguridad y data perimeters.

---

## Benefits

- **No Internet exposure** — El tráfico permanece dentro de la red de AWS
- **Reduced attack surface** — Sin rutas públicas de red
- **Compliance** — Facilita cumplimiento de regulaciones de data residency
- **Lower latency** — Comunicación más rápida dentro de la misma región

---

## Prerequisites

- Cuenta de AWS con acceso a VPC
- Kiro Enterprise subscription
- VPC configurada en la región donde está tu Kiro Profile

---

## Configuration Steps

### 1. Create the VPC Endpoint

```bash
aws ec2 create-vpc-endpoint \
  --vpc-id vpc-xxxxxxxx \
  --service-name com.amazonaws.us-east-1.kiro \
  --vpc-endpoint-type Interface \
  --subnet-ids subnet-xxxxxxxx \
  --security-group-ids sg-xxxxxxxx
```

### 2. Configure DNS Resolution

Habilitar **Private DNS** para que el endpoint resuelva el dominio de Kiro automáticamente:

```bash
aws ec2 modify-vpc-endpoint \
  --vpc-endpoint-id vpce-xxxxxxxx \
  --private-dns-enabled
```

### 3. Update Security Groups

Asegurate de que el security group del endpoint permite tráfico desde las instancias que usan Kiro CLI:

```
Inbound:  TCP 443 from your instances/subnets
Outbound: TCP 443 to Kiro service
```

---

## Verification

```bash
# Verificar que el traffic va por el endpoint privado
kiro-cli doctor --all

# Ver el endpoint configurado
aws ec2 describe-vpc-endpoints --filters "Name=service-name,Values=*kiro*"
```

---

## Network Architecture

```
[Kiro CLI] → [VPC Subnet] → [VPC Endpoint] → [AWS PrivateLink] → [Kiro Service]
                                                    ↑
                                            Sin salida a Internet
```

---

## Enterprise Admin Notes

Los administradores Enterprise pueden forzar el uso de VPC endpoints para todos los usuarios de su organización desde la **Kiro Console → Settings**.

---

## Related

- [Firewalls and Proxies →](./05_Firewalls, proxies, and data perimeters.md)
- [Enterprise Governance →](../14_Enterprise/06_Governance.md)
- [AWS PrivateLink documentation →](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html)