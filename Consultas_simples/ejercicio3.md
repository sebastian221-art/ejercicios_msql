# ejercicios_msql
-- Ejercicio Empleados contratados en los últimos 2 años
SELECT 
    id_empleado,
    nombre,
    fecha_contratacion,
    TIMESTAMPDIFF(YEAR, fecha_contratacion, CURDATE()) AS años_en_empresa
FROM 
    Empleados
WHERE 
    fecha_contratacion >= DATE_SUB(CURDATE(), INTERVAL 2 YEAR)
ORDER BY 
    fecha_contratacion DESC;
CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100)
);

CREATE TABLE Empleados (
    id_empleado INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    fecha_contratacion DATE NOT NULL,
    salario DECIMAL(10,2) NOT NULL
);