# Matriz de Accesos

## Objetivo

Definir los permisos de acceso a los recursos implementados en AWS aplicando el principio de mínimo privilegio (Least Privilege), garantizando la seguridad de la infraestructura y evitando accesos no autorizados.

---

# Principio de Mínimo Privilegio

Todos los usuarios, roles y servicios cuentan únicamente con los permisos estrictamente necesarios para realizar sus funciones.

No se utiliza la cuenta **Root** para operaciones diarias.

---

# Matriz de Accesos

| Recurso | Usuario / Rol | Método de Acceso | Permisos | Restricciones |
|----------|---------------|------------------|-----------|---------------|
| Amazon EC2 | role-ec2-wordpress | AWS Systems Manager Session Manager | Administración de la instancia | Sin acceso SSH público |
| Amazon EC2 | usuario-administrador | Consola AWS | Administración completa | MFA habilitado |
| Amazon EC2 | usuario-devops | Consola AWS | Inicio, detención y consulta | Sin permisos de eliminación |
| Amazon RDS | EC2 WordPress | MySQL (Puerto 3306) | Lectura y escritura | Solo desde Security Group de EC2 |
| Amazon RDS | usuario-administrador | Consola AWS | Administración | Sin acceso público |
| Amazon S3 | role-ec2-wordpress | IAM Role | GetObject y PutObject | Bucket privado |
| Amazon CloudWatch | role-cloudwatch-agent | IAM Role | Publicación de métricas y logs | Solo métricas del proyecto |
| Consola AWS | usuario-administrador | IAM + MFA | Acceso completo | MFA obligatorio |
| Consola AWS | usuario-devops | IAM | Solo lectura de monitoreo | Acceso restringido |

---

# Roles IAM Implementados

## role-ec2-wordpress

Permisos:

- s3:GetObject
- s3:PutObject
- ssm:*
- cloudwatch:PutMetricData

Uso:

Permite que las instancias EC2 interactúen con Amazon S3, CloudWatch y Session Manager sin utilizar claves de acceso.

---

## role-cloudwatch-agent

Permisos:

- cloudwatch:PutMetricData
- logs:CreateLogStream
- logs:PutLogEvents

Uso:

Envía métricas y registros del sistema hacia Amazon CloudWatch.

---

## usuario-devops

Permisos:

- EC2 Describe
- EC2 Start
- EC2 Stop
- RDS Describe
- S3 Read Only
- CloudWatch Read Only

No puede eliminar recursos.

---

## usuario-administrador

Permisos:

Administrador completo de la infraestructura.

Incluye autenticación multifactor (MFA).

---

# Seguridad Aplicada

Se implementaron las siguientes medidas:

- Acceso mediante IAM.
- MFA para administradores.
- Session Manager en lugar de SSH público.
- Security Groups con acceso restringido.
- Base de datos en subred privada.
- Bucket S3 sin acceso público.
- Cifrado de almacenamiento mediante AWS KMS y SSE-S3.
- Comunicación segura mediante HTTPS y SSL.

---

# Conclusión

La matriz de accesos implementada garantiza que cada recurso únicamente pueda ser utilizado por los usuarios o servicios autorizados, reduciendo significativamente la superficie de ataque y cumpliendo las recomendaciones del AWS Well-Architected Framework.