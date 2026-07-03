# Justificación de la Arquitectura

## Descripción General

La arquitectura implementada para el proyecto **Comercial Nova** fue diseñada siguiendo las buenas prácticas del **AWS Well-Architected Framework**, priorizando disponibilidad, seguridad, escalabilidad y optimización de costos.

La solución separa claramente la capa de presentación, la lógica de aplicación y la capa de datos, permitiendo que cada componente pueda escalar y administrarse de forma independiente.

---

## Componentes Principales

La infraestructura está compuesta por los siguientes servicios:

- Amazon VPC
- Application Load Balancer (ALB)
- Amazon EC2
- Auto Scaling Group
- Amazon RDS MySQL
- Amazon S3
- NAT Gateway
- AWS IAM
- Amazon CloudWatch

---

## Justificación Técnica

### Amazon VPC

Se creó una VPC dedicada para aislar completamente la infraestructura del proyecto del resto de recursos de AWS.

La red fue dividida en subredes públicas y privadas distribuidas en dos Zonas de Disponibilidad (Availability Zones), mejorando la disponibilidad del sistema.

---

### Application Load Balancer

El ALB distribuye automáticamente el tráfico HTTP entre las instancias EC2 disponibles.

Beneficios:

- Balanceo automático de carga.
- Eliminación de instancias no saludables.
- Alta disponibilidad.
- Punto único de acceso al sitio WordPress.

---

### Amazon EC2

Las instancias EC2 alojan el servidor web Apache, PHP y WordPress.

Se implementó un Auto Scaling Group para que AWS agregue o elimine instancias según la demanda.

Ventajas:

- Escalabilidad automática.
- Mayor disponibilidad.
- Mejor rendimiento ante picos de tráfico.

---

### Amazon RDS

La base de datos se implementó utilizando Amazon RDS para MySQL.

Se eligió esta opción porque ofrece:

- Administración automática.
- Backups.
- Actualizaciones automáticas.
- Alta disponibilidad mediante Multi-AZ.
- Mayor seguridad al mantenerse en subred privada.

---

### Amazon S3

Se utiliza para almacenar:

- Archivos multimedia de WordPress.
- Copias de seguridad.
- Logs del sistema.

Esto evita almacenar archivos directamente en las instancias EC2, facilitando el escalado horizontal.

---

### IAM

Se aplicó el principio de mínimo privilegio.

Los roles permiten que las instancias EC2 accedan únicamente al bucket S3 y a CloudWatch sin utilizar claves de acceso almacenadas.

---

### Amazon CloudWatch

CloudWatch permite monitorear continuamente:

- CPU
- Memoria
- Conexiones
- Red
- Estado del Load Balancer
- Estado de RDS

Además se configuraron alarmas para detectar problemas antes de afectar el servicio.

---

## Beneficios de la Arquitectura

- Alta disponibilidad.
- Escalabilidad automática.
- Separación entre aplicación y base de datos.
- Seguridad mediante redes privadas.
- Monitoreo continuo.
- Optimización de almacenamiento mediante S3.
- Arquitectura preparada para crecimiento futuro.

---

## Conclusión

La arquitectura implementada cumple los objetivos del proyecto al proporcionar una plataforma WordPress segura, escalable, altamente disponible y alineada con las buenas prácticas recomendadas por AWS.