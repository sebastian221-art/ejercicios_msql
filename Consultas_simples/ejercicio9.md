# ejercicios_msql
-- Ejercicio Los 3 productos más caros
SELECT 
    id_producto,
    nombre,
    descripcion,
    precio_actual
FROM 
    Productos
ORDER BY 
    precio_actual DESC
LIMIT 3;
CREATE TABLE Productos (
    id_producto INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    precio DECIMAL(10,2) NOT NULL
);