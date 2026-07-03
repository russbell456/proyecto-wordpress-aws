# Inventario de Recursos AWS

## Información General

Proyecto: Comercial Nova

Plataforma: WordPress sobre Amazon Web Services

Región: us-east-1 (N. Virginia)

---

# Recursos Implementados

## Amazon VPC

- 1 VPC
- CIDR: 10.0.0.0/16

---

## Subredes

- subnet-public-1a
- subnet-public-1b
- subnet-private-1a
- subnet-private-1b

---

## Internet Gateway

- 1 Internet Gateway

Asociado a la VPC principal.

---

## NAT Gateway

- 1 NAT Gateway

Utilizado para permitir acceso a Internet desde las subredes privadas.

---

## Amazon EC2

Cantidad mínima:

- 2 instancias

Tipo:

- t3.micro

Sistema Operativo:

- Amazon Linux 2023

---

## Application Load Balancer

Cantidad:

- 1

Función:

Distribuir tráfico HTTP entre las instancias EC2.

---

## Auto Scaling Group

Configuración:

- Mínimo: 2 instancias
- Deseado: 2
- Máximo: 4

---

## Amazon RDS

Motor:

MySQL 8.0

Clase:

db.t3.micro

Configuración:

Multi-AZ

---

## Amazon S3

Bucket destinado para:

- Medios
- Backups
- Logs

Versionado habilitado.

Acceso público bloqueado.

---

## AWS IAM

Roles implementados:

- role-ec2-wordpress
- role-cloudwatch-agent

Usuarios:

- usuario-administrador
- usuario-devops

---

## Amazon CloudWatch

Recursos monitoreados:

- EC2
- ALB
- RDS

Alarmas configuradas:

- CPU Alta
- Espacio Libre RDS

---

# Estado General

Todos los recursos fueron implementados correctamente y forman parte de la arquitectura utilizada para el despliegue de WordPress en AWS.