# Matriz de Accesos y Seguridad (Security Groups)

Aplicando el **principio de mínimo privilegio**, se definen las siguientes reglas perimetrales para los componentes de la infraestructura de Comercial Nova.

### 1. Security Group: ALB (Load Balancer público)
* **Descripción:** Permite la entrada de tráfico web desde el internet público.
* **Reglas de Entrada (Inbound):**
  | Protocolo | Puerto | Origen | Propósito |
  |-----------|--------|--------|-----------|
  | TCP (HTTP)| 80     | 0.0.0.0/0 | Acceso web inicial |
  | TCP (HTTPS)| 443   | 0.0.0.0/0 | Acceso web seguro (si aplica certificado) |

### 2. Security Group: EC2 (Capa Web/App WordPress)
* **Descripción:** Solo permite tráfico web que provenga estrictamente del balanceador y acceso SSH controlado.
* **Reglas de Entrada (Inbound):**
  | Protocolo | Puerto | Origen | Propósito |
  |-----------|--------|--------|-----------|
  | TCP | 80 / 443 | sg-ALB (Security Group del ALB) | Tráfico balanceado legítimo |
  | TCP (SSH) | 22 | Mi_IP_Pública / Session Manager | Administración segura y restringida |

### 3. Security Group: RDS (Base de Datos)
* **Descripción:** Aislamiento total de la base de datos. No tiene exposición a Internet.
* **Reglas de Entrada (Inbound):**
  | Protocolo | Puerto | Origen | Propósito |
  |-----------|--------|--------|-----------|
  | TCP (MySQL)| 3306 | sg-EC2 (Security Group de las EC2) | Únicamente consultas de la aplicación |