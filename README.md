# Caso de Estudio Final - Implementación de WordPress en AWS
**Curso:** Virtualización de servicios tecnológicos  
**Institución:** Universidad Peruana Unión (UPeU)  
**Cliente:** Comercial Nova  

---

## 👥 Integrantes y Roles
* **Russbell Daniel Cari Mamani** - Consultor de Infraestructura Cloud, Automatización y Seguridad (Responsable de SonarCloud, Redes y Base de Datos).

## 📌 Problema Planteado y Alcance
Comercial Nova es una empresa en crecimiento que requiere la implementación de un nuevo portal web corporativo utilizando WordPress en la nube de AWS. El proyecto tiene como alcance diseñar y desplegar una arquitectura altamente disponible, segura, escalable y con un monitoreo robusto, mitigando los costos mediante prácticas de optimización cloud.

## 🏗️ Arquitectura Propuesta
La solución consta de una arquitectura multi-capa distribuida en múltiples Zonas de Disponibilidad (Multi-AZ):
* **Capa de Red:** Amazon VPC propia segmentada en subredes públicas y privadas.
* **Capa de Cómputo:** Instancias Amazon EC2 autoadministradas mediante un Auto Scaling Group.
* **Capa de Balanceo:** Application Load Balancer (ALB) para distribuir el tráfico público HTTP/HTTPS.
* **Capa de Datos:** Amazon RDS (MySQL/MariaDB) alojado en subredes privadas aisladas.
* **Capa de Almacenamiento:** Amazon S3 para la persistencia del contenido multimedia de WordPress.

*(Enlace al diagrama: [Ver Diagrama](./arquitectura/diagrama.png))*

## 🛠️ Servicios Cloud Utilizados
1. **Amazon VPC:** Para el aislamiento y segmentación de la red.
2. **Amazon EC2:** Para el procesamiento y ejecución del Stack web (Linux + Apache/Nginx + PHP).
3. **Amazon RDS:** Base de datos administrada con alta disponibilidad y backups automáticos.
4. **Amazon S3:** Almacenamiento desacoplado y versionado para archivos estáticos.
5. **Elastic Load Balancing & Auto Scaling:** Alta disponibilidad frente a picos de demanda.
6. **AWS CloudWatch:** Centralización de métricas y alertas operacionales.
7. **AWS IAM:** Gestión de identidades y accesos bajo el principio de mínimo privilegio.

---
*Nota: Este proyecto se despliega bajo el entorno de AWS Academy con fines académicos.*