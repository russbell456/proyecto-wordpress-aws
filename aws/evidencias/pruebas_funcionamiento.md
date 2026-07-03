# Pruebas de Funcionamiento

## Objetivo

Verificar el correcto funcionamiento de todos los componentes de la arquitectura implementada en AWS.

---

# Prueba 1

## Acceso al sitio Web

Descripción

Ingresar desde un navegador a la URL pública del sitio WordPress.

Resultado esperado

La página principal carga correctamente.

Estado

✅ Correcto

---

# Prueba 2

## Inicio de Sesión

Descripción

Ingresar al panel administrativo mediante:

```
http://IP/wp-admin
```

Resultado esperado

Acceso exitoso al panel de administración.

Estado

✅ Correcto

---

# Prueba 3

## Publicación de Contenido

Descripción

Crear una nueva entrada en WordPress.

Resultado esperado

La publicación aparece correctamente en el sitio web.

Estado

✅ Correcto

---

# Prueba 4

## Conexión con Amazon RDS

Descripción

Registrar una nueva entrada y verificar que permanezca almacenada.

Resultado esperado

Los datos se almacenan correctamente en la base de datos.

Estado

✅ Correcto

---

# Prueba 5

## Almacenamiento en Amazon S3

Descripción

Subir una imagen desde WordPress.

Resultado esperado

El archivo se almacena correctamente en el bucket S3.

Estado

✅ Correcto

---

# Prueba 6

## Balanceador de Carga

Descripción

Acceder varias veces al sitio para comprobar la distribución del tráfico.

Resultado esperado

El ALB responde correctamente y mantiene disponible el sitio.

Estado

✅ Correcto

---

# Prueba 7

## Monitoreo

Descripción

Verificar las métricas desde Amazon CloudWatch.

Resultado esperado

Las métricas de EC2, ALB y RDS se visualizan correctamente.

Estado

✅ Correcto

---

# Resultado General

Todas las pruebas fueron ejecutadas satisfactoriamente, comprobando el correcto funcionamiento de la infraestructura desplegada sobre Amazon Web Services y la disponibilidad del sitio WordPress.