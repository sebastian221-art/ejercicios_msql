# ejercicios_msql
-- Ejercicio Salario promedio de empleados
SELECT 
    AVG(salario_actual) AS salario_promedio,
    MIN(salario_actual) AS salario_minimo,
    MAX(salario_actual) AS salario_maximo
FROM 
    Empleados;
CREATE TABLE Empleados (
    id_empleado INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    salario DECIMAL(10,2) NOT NULL
);