# Alertas Configuradas en Amazon CloudWatch

## Objetivo

Monitorear continuamente el estado de la infraestructura implementada en AWS y generar alertas automáticas cuando alguna métrica supere los umbrales definidos.

---

# Servicio Utilizado

Amazon CloudWatch

---

# Alarmas Configuradas

## 1. CPU Alta EC2

Nombre:

```
alarm-ec2-cpu-alta
```

Configuración

| Parámetro | Valor |
|-----------|-------|
| Recurso | Amazon EC2 |
| Métrica | CPUUtilization |
| Umbral | Mayor al 80 % |
| Tiempo | 5 minutos |
| Acción | Notificación mediante Amazon SNS |

Objetivo

Detectar una utilización elevada del procesador que pueda afectar el rendimiento del sitio WordPress.

---

## 2. Espacio Disponible en Amazon RDS

| Parámetro | Valor |
|-----------|-------|
| Recurso | Amazon RDS |
| Métrica | FreeStorageSpace |
| Umbral | Menor a 2 GB |
| Acción | Notificación mediante Amazon SNS |

Objetivo

Detectar oportunamente falta de espacio disponible en la base de datos.

---

## 3. Estado del Application Load Balancer

Métricas monitoreadas:

- RequestCount
- TargetResponseTime
- HealthyHostCount

Objetivo

Verificar que las instancias registradas permanezcan saludables y continúen respondiendo correctamente.

---

# Notificaciones

Las alarmas envían notificaciones utilizando Amazon SNS al correo del administrador del proyecto.

---

# Beneficios

- Detección temprana de problemas.
- Monitoreo continuo.
- Respuesta rápida ante incidentes.
- Mejora de la disponibilidad del servicio.
- Apoyo al Auto Scaling.

---

# Evidencias Recomendadas

Agregar las siguientes capturas:

- Dashboard de CloudWatch.
- Alarma alarm-ec2-cpu-alta.
- Estado OK de las alarmas.
- Historial de métricas.

---

# Conclusión

Las alarmas configuradas permiten detectar problemas de rendimiento y disponibilidad antes de que impacten a los usuarios finales, mejorando la confiabilidad de la infraestructura desplegada en AWS.