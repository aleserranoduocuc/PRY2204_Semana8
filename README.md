# PRY2204 - Semana 8 - Taller Mecánico Mikes Ltda.

## 📋 Actividad Sumativa

**Alumno:** Alejandro Serrano  
**Asignatura:** PRY2204 - Modelamiento de Bases de Datos  
**Institución:** Duoc UC Online  
**Fecha:** 29/09/2026  
**Base de datos:** Oracle Autonomous Database (Oracle Cloud)  
**Usuario BD:** `PRY2204_S8`

---

## 🎯 Objetivo

Implementar el modelo relacional del sistema de gestión de mantenciones automotrices del **Taller Mecánico Mikes Ltda.**, incluyendo:

- Creación de tablas con restricciones de integridad (DDL)
- Definición de reglas de negocio mediante `ALTER TABLE`
- Poblamiento de datos usando secuencias e identity
- Generación de informes con `SELECT`, filtros y `ORDER BY`

---

## 📂 Contenido del repositorio

| Archivo | Descripción |
|---------|-------------|
| `Exp3_S8_AlejandroSerrano.sql` | Script completo con DDL, DML y consultas |
| `README.md` | Este documento |

---

## 🏗️ Estructura del script

### 🔹 Caso 1: Creación de tablas (DDL)

Se crean **14 tablas** en orden secuencial (fuertes → débiles):

1. `pais` — Identity (inicia en 9, +3)
2. `servicio`
3. `marca`
4. `tipo_automovil`
5. `mecanico` — Identity (inicia en 460, +7)
6. `ciudad` — FK a pais
7. `sucursal` — FK a ciudad
8. `modelo` — FK a marca, tipo_automovil
9. `cliente` — FK a ciudad
10. `automovil` — FK a cliente, modelo
11. `mantencion` — PK compuesta (nro_mantencion, id_sucursal)
12. `detalle_servicio` — PK compuesta
13. `estandar` — FK a cliente
14. `premium` — FK a cliente

**Restricciones incluidas:**
- PK (Primary Key)
- FK (Foreign Key)
- UN (Unique)
- CK (Check)

---

### 🔹 Caso 2: Reglas de negocio (ALTER TABLE)

| Regla | Constraint |
|-------|------------|
| Email único en CLIENTE | `cliente_email_un` (UNIQUE) |
| DV del RUT válido (0-9, K) | `cliente_dv_ck` (CHECK) |
| Sueldo mínimo mecánico: $510.000 | `mecanico_sueldo_ck` (CHECK) |
| Estados válidos de mantención | `mantencion_estado_ck` (CHECK) |

---

### 🔹 Caso 3: Poblamiento de datos

Se pueblan las siguientes tablas:

| Tabla | Filas | Método |
|-------|-------|--------|
| `pais` | 3 | Identity (9, 12, 15) |
| `servicio` | 4 | Sequence (400, 402, 404, 406) |
| `ciudad` | 3 | Sequence (165, 170, 175) |
| `sucursal` | 3 | Manual |
| `mecanico` | 10 | Identity (460, 467, ..., 523) |

---

### 🔹 Caso 4: Informes

**Informe 1:** Simulación de rebaja selectiva de impuestos  
- Mecánicos con `bono_jefatura IS NULL` y `monto_impuestos < 40000`
- Ordenado por `impuesto_actual DESC` y `apaterno ASC`

**Informe 2:** Ajuste salarial del 5%  
- Mecánicos con sueldo entre $600.000 y $900.000, o sin supervisor
- Ordenado por `salario ASC` y `nombre DESC`

---

## 🛠️ Tecnologías utilizadas

- **Oracle Autonomous Database** (Oracle Cloud)
- **Oracle SQL Developer Web**
- **SQL** (DDL, DML, SELECT)
- **GitHub** (control de versiones)

---

## 🚀 Cómo ejecutar

1. Conectarse a Oracle Cloud con el usuario `ADMIN`.
2. Abrir **Database Actions → SQL**.
3. Ejecutar el script `Exp3_S8_AlejandroSerrano.sql` completo con `F5`.

> ⚠️ El script incluye `ALTER SESSION SET CURRENT_SCHEMA = PRY2204_S8;` al inicio para asegurar que todos los objetos se creen en el esquema correcto.

---

## 📊 Resultados

El script genera exitosamente:

- ✅ 14 tablas creadas
- ✅ 4 constraints de negocio
- ✅ 23 filas insertadas
- ✅ 2 secuencias creadas
- ✅ 2 informes con formato y orden solicitado

---

**Duoc UC Online — 2026**
