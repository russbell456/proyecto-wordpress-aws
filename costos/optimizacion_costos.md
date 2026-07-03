# Optimización de Costos

## Objetivo

Analizar el costo estimado de la infraestructura implementada en AWS e identificar oportunidades para reducir el gasto mensual sin afectar la disponibilidad ni el funcionamiento del sistema.

---

# Estimación de Costos

| Servicio | Configuración | Costo Mensual Aproximado |
|-----------|---------------|--------------------------|
| Amazon EC2 | 2 x t3.micro | $15.18 |
| Application Load Balancer | 1 ALB | $19.80 |
| Amazon RDS | db.t3.micro Multi-AZ | $32.40 |
| Amazon S3 | 15 GB | $1.20 |
| NAT Gateway | 1 NAT Gateway | $34.20 |
| Transferencia de datos | 20 GB | $1.80 |
| Amazon CloudWatch | Dashboard + Alarmas | $4.50 |

## Costo Total

**Costo mensual estimado: USD 109.08**

---

# Servicios de Mayor Costo

Los servicios que representan el mayor porcentaje del costo son:

- NAT Gateway
- Amazon RDS Multi-AZ
- Application Load Balancer

Estos tres servicios representan aproximadamente el 79 % del costo total de la infraestructura.

---

# Estrategias de Optimización

## 1. Rightsizing de EC2

Monitorear el consumo de CPU y memoria para determinar si las instancias pueden migrarse a una configuración de menor costo.

**Ahorro estimado:** 3 USD/mes

---

## 2. Optimización del NAT Gateway

En ambientes de laboratorio puede reemplazarse por una NAT Instance o apagarse cuando no se utilice.

**Ahorro estimado:** 25–30 USD/mes

---

## 3. Lifecycle en Amazon S3

Mover automáticamente archivos antiguos hacia clases de almacenamiento de menor costo:

- S3 Standard-IA
- Glacier Instant Retrieval

**Ahorro estimado:** 0.30–0.50 USD/mes

---

## 4. Apagado Automático

Programar el apagado de instancias EC2 y RDS fuera del horario de trabajo mediante AWS Instance Scheduler.

**Ahorro estimado:** 10–15 USD/mes

---

## 5. Savings Plans

Para ambientes productivos se recomienda utilizar Savings Plans o Reserved Instances para EC2 y RDS.

**Ahorro estimado:** entre 15 % y 30 %

---

# Comparación

| Arquitectura | Costo |
|--------------|--------|
| Arquitectura Inicial | USD 109.08 |
| Arquitectura Optimizada | USD 65–70 |

La optimización permite reducir aproximadamente entre un **35 % y 40 %** del costo mensual.

---

# Conclusión

Aplicando estas estrategias es posible mantener una infraestructura altamente disponible reduciendo considerablemente el costo operativo mensual.