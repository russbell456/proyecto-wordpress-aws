# Justificación Técnica de la Arquitectura - Comercial Nova

Este documento detalla los fundamentos técnicos y las decisiones de diseño cloud adoptadas para satisfacer los requerimientos de disponibilidad, seguridad, escalabilidad y costo de la empresa.

### 1. Segmentación de Red (Amazon VPC)
* **Decisión:** Creación de una VPC propia con un bloque CIDR `/16` (ej. `10.0.0.0/16`), dividida en subredes públicas (`/24`) y privadas (`/24`) en dos Zonas de Disponibilidad (Multi-AZ).
* **Justificación:** El aislamiento perimetral garantiza que la base de datos (RDS) y la lógica de aplicación crítica no queden expuestas directamente a Internet. Las subredes públicas albergarán únicamente el Application Load Balancer (ALB).

### 2. Alta Disponibilidad (Multi-AZ) y Cómputo (EC2)
* **Decisión:** Despliegue de un mínimo de 2 instancias EC2 distribuidas en diferentes zonas de disponibilidad sincronizadas detrás de un Application Load Balancer (ALB) y gestionadas por un Auto Scaling Group (ASG).
* **Justificación:** Si una zona de disponibilidad sufre una caída (corte de energía, falla de hardware de AWS), el ALB redirigirá inmediatamente el 100% del tráfico hacia la instancia de la zona activa. El ASG garantiza el "Auto-healing" (reemplazo automático de instancias no saludables).

### 3. Capa de Datos Desacoplada (Amazon RDS)
* **Decisión:** Uso de Amazon RDS (MySQL/MariaDB) en modo Multi-AZ o con respaldos automatizados activos en subredes privadas.
* **Justificación:** Separar la base de datos del servidor web (EC2) evita el "Single Point of Failure" (Punto único de falla). RDS gestiona los parches de seguridad, optimización de almacenamiento y realiza copias de seguridad automáticas diarias durante una ventana de bajo tráfico configurada.

### 4. Persistencia de Medios Desacoplada (Amazon S3)
* **Decisión:** Externalización del directorio `/wp-content/uploads` de WordPress hacia un bucket de Amazon S3 configurado con acceso privado y versionado activo.
* **Justificación:** Al usar múltiples instancias EC2 dinámicas (que pueden crearse y destruirse por el Auto Scaling), el almacenamiento local de la EC2 se vuelve efímero. Amazon S3 actúa como un almacenamiento centralizado, de alta durabilidad (99.999999999%) e infinitamente escalable, asegurando que las imágenes subidas por Comercial Nova nunca se pierdan.

### 5. Monitoreo Temprano (Amazon CloudWatch)
* **Decisión:** Implementación de métricas de uso de CPU y alarmas operacionales basadas en umbrales (ej. >80% de utilización sostenida por 5 minutos).
* **Justificación:** Permite identificar cuellos de botella de manera proactiva, alertando al equipo técnico antes de que el portal de la empresa experimente degradación de servicio o indisponibilidad.