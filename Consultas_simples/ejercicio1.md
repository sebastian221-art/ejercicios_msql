# ejercicios_msql
-- Ejercicio  Productos con precio mayor a $50
SELECT 
    id_producto,
    nombre,
    descripcion,
    precio_actual AS precio
FROM 
    Productos
WHERE 
    precio_actual > 50
ORDER BY 
    precio_actual DESC;
CREATE TABLE Productos (
    id_producto INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    descripcion TEXT,
    precio DECIMAL(10,2) NOT NULL,
    id_proveedor INT NOT NULL,
    id_tipo INT NOT NULL,
    stock INT NOT NULL DEFAULT 0
);