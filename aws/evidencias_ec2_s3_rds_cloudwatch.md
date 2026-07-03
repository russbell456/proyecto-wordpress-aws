# Evidencias de EC2, S3, RDS y CloudWatch

## Objetivo

Documentar las evidencias del correcto funcionamiento de los principales servicios implementados en AWS.

---

# Amazon EC2

## Evidencia

Agregar captura donde se observe:

- Instancias en estado Running.
- Nombre de las instancias.
- Dirección IP.
- Security Groups.
- Nombre del estudiante.
- Hora del sistema.

Resultado esperado:

Las instancias deben aparecer en estado **Running**.

---

# Amazon S3

## Evidencia

Agregar captura mostrando:

- Bucket creado.
- Versionado habilitado.
- Block Public Access activado.
- Carpetas media, backups y logs.

Resultado esperado:

Bucket disponible y accesible únicamente mediante IAM.

---

# Amazon RDS

## Evidencia

Agregar captura mostrando:

- Estado Available.
- Motor MySQL.
- Multi-AZ.
- Endpoint.
- Almacenamiento.

Resultado esperado:

La base de datos debe permanecer disponible y conectada correctamente con WordPress.

---

# Amazon CloudWatch

## Evidencia

Agregar captura del Dashboard mostrando:

- CPUUtilization
- NetworkIn
- NetworkOut
- RequestCount
- TargetResponseTime
- DatabaseConnections
- FreeStorageSpace

También incluir la alarma:

alarm-ec2-cpu-alta

Resultado esperado:

Las métricas deben encontrarse en estado normal y las alarmas en estado **OK**.

---

# Observaciones

Todas las capturas deben incluir:

- Nombre del estudiante.
- Hora del sistema.
- Consola oficial de AWS.