# T41A-P04

# 📘 Propiedades de las Relaciones y Álgebra Relacional en PostgreSQL

## 🧩 1. Propiedades de las Relaciones
En PostgreSQL, una reLas propiedades fundamentales que debe cumplir son:

🔹 Propiedades
- Nombre único: Cada tabla tiene un nombre distinto.
- Atributos únicos: No se permiten columnas con el mismo nombre.
- Tuplas únicas: Se garantiza con claves primarias o restricciones UNIQUE.
- Valores atómicos: Cada celda contiene un valor indivisible.
- Orden irrelevante: El orden de filas y columnas no afecta la lógica.
- Dominio definido: Cada columna tiene un tipo de dato (INTEGER, TEXT, etc.).

---

## 🧮 2. Operadores de Álgebra Relacional en PostgreSQL
PostgreSQL implementa los operadores del álgebra relacional mediante SQL. Aquí están los más importantes:

| Álgebra Relacional         | PostgreSQL SQL         | Ejemplo                                                                 |
|----------------------------|------------------------|-------------------------------------------------------------------------|
| Selección (σ)              | WHERE                  | `SELECT * FROM empleados WHERE salario > 30000;`                        |
| Proyección (π)             | SELECT columnas        | `SELECT nombre FROM empleados;`                                        |
| Unión (∪)                  | UNION                  | `SELECT nombre FROM A UNION SELECT nombre FROM B;`                     |
| Intersección (∩)           | INTERSECT              | `SELECT nombre FROM A INTERSECT SELECT nombre FROM B;`                 |
| Diferencia (−)             | EXCEPT                 | `SELECT nombre FROM A EXCEPT SELECT nombre FROM B;`                    |
| Producto cartesiano (×)    | FROM A, B              | `SELECT * FROM A, B;`                                                  |
| Join (⨝)                   | JOIN ON                | `SELECT * FROM A JOIN B ON A.id = B.id;`                               |
| Renombramiento (ρ)         | AS                     | `SELECT nombre AS empleado_nombre FROM empleados;`                     |

--- 

🧱 Tablas de ejemplo

Tabla empleados
```sql
CREATE TABLE empleados (
    id INT PRIMARY KEY,
    nombre VARCHAR(50),
    salario INT,
    departamento_id INT
);
```
Tabla departamentos

```sql
CREATE TABLE departamentos (
    id INT PRIMARY KEY,
    nombre VARCHAR(50)
);
```

📥 Inserción de datos
Datos para empleados

```sql
INSERT INTO empleados (id, nombre, salario, departamento_id) VALUES
(1, 'Ana', 28000, 1),
(2, 'Luis', 32000, 2),
(3, 'Carlos', 40000, 1),
(4, 'Marta', 25000, 3),
(5, 'Sofía', 50000, 2);
```

Datos para departamentos
```sql
INSERT INTO departamentos (id, nombre) VALUES
(1, 'Ventas'),
(2, 'Marketing'),
(3, 'Recursos Humanos');
```

🔹 1. Selección (σ)
Ejercicio: Obtener todos los empleados que ganan más de 2500.

🔹 2. Proyección (π)
Ejercicio: Mostrar solo los nombres de los departamentos

🔹 3. Producto cartesiano (×)
Ejercicio: Combinar todos los empleados con todos los departamentos (sin relación).

🔹 4. Join (⨝)
Ejercicio: Mostrar el nombre del empleado junto con el nombre de su departamento.

🔹 5. Renombramiento (ρ)
Ejercicio: Renombrar la tabla empleados como e y mostrar sus datos.

🔹 6. Unión (∪)
Ejercicio: Supón que tienes otra tabla empleados_nuevos. Une ambas tablas.

🔹 7. Intersección (∩)
Ejercicio: Obtener empleados que están en ambas tablas empleados y empleados_nuevos.

🔹 8. Diferencia (−)
Ejercicio: Obtener empleados que están en empleados pero no en empleados_nuevos.

🔹 9. Agregación
Ejercicio: Calcular el salario promedio por departamento.

```sql
SELECT departamento_id, AVG(salario) AS salario_promedio
FROM empleados
GROUP BY departamento_id;
```

🔹 10. Subconsulta
Ejercicio: Mostrar empleados que ganan más que el salario promedio.

```sql
SELECT * FROM empleados
WHERE salario > (
    SELECT AVG(salario) FROM empleados
);
```
