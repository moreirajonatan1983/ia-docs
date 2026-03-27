# Puntos de enlace de la VPC (AWS PrivateLink)

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/vpc-endpoints/](https://kiro.dev/docs/cli/privacy-and-security/vpc-endpoints/)

---

## Descripción general

**AWS PrivateLink** permite que Kiro CLI se comunique con los servicios de AWS sin que el tráfico salga a Internet público. Ideal para organizaciones con requisitos estrictos de seguridad y perímetros de datos.

---

## Beneficios

- **Sin exposición a Internet** — El tráfico permanece dentro de la red de AWS
- **Superficie de ataque reducida** — Sin rutas públicas de red
- **Cumplimiento** — Facilitar el cumplimiento de las regulaciones de residencia de datos
- **Menor latencia** — Comunicación más rápida dentro de la misma región

---

## Requisitos previos

- Cuenta de AWS con acceso a VPC
- Suscripción Kiro Enterprise
- VPC configurada en la región donde está tu perfil Kiro

---

## Pasos de configuración

### 1. Cree el endpoint de la VPC

```bash
aws ec2 create-vpc-endpoint \
  --vpc-id vpc-xxxxxxxx \
  --service-name com.amazonaws.us-east-1.kiro \
  --vpc-endpoint-type Interface \
  --subnet-ids subnet-xxxxxxxx \
  --security-group-ids sg-xxxxxxxx
```

### 2. Configurar la resolución DNS

Habilitar **DNS privado** para que el endpoint resuelva el dominio de Kiro automáticamente:

```bash
aws ec2 modify-vpc-endpoint \
  --vpc-endpoint-id vpce-xxxxxxxx \
  --private-dns-enabled
```

### 3. Actualizar grupos de seguridad

Asegúrese de que el grupo de seguridad del endpoint permita el tráfico desde las instancias que usan Kiro CLI:

```
Inbound:  TCP 443 from your instances/subnets
Outbound: TCP 443 to Kiro service
```

---

## Verificación

```golpecito
# Verificar que el tráfico va por el endpoint privado
kiro-cli doctor --todos

# Ver el endpoint configurado
aws ec2 describe-vpc-endpoints --filters "Nombre=nombre-servicio,Valores=*kiro*"
```

---

## Arquitectura de red

```
[Kiro CLI] → [VPC Subnet] → [VPC Endpoint] → [AWS PrivateLink] → [Kiro Service]
                                                    ↑
                                            Sin salida a Internet
```

---

## Notas de administración empresarial

Los administradores Enterprise pueden forzar el uso de endpoints de VPC para todos los usuarios de su organización desde la **Kiro Console → Configuración**.

---

## Relacionado

- [Firewalls y Proxies →](./05_Firewalls, proxies y perímetros de datos.md)
- [Gobierno empresarial →](../14_Enterprise/06_Governance.md)
- [Documentación de AWS PrivateLink →](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html)