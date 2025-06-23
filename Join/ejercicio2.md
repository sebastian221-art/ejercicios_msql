 ejercicios_msql
-- Ejercicio Productos y sus proveedores
SELECT 
    pr.id_producto,
    pr.nombre AS producto,
    pr.descripcion,
    pr.precio_actual,
    p.nombre AS proveedor,
    p.ruc AS ruc_proveedor
FROM 
    Productos pr
INNER JOIN 
    Proveedores p ON pr.id_proveedor = p.id_proveedor
ORDER BY 
    p.nombre, pr.nombre;


CREATE TABLE Proveedores (
    id_proveedor INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE Productos (
    id_producto INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    id_proveedor INT NOT NULL,
    FOREIGN KEY (id_proveedor) REFERENCES Proveedores(id_proveedor)
);