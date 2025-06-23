# ejercicios_msql
-- Ejercicio Proveedores con más de 5 productos
SELECT 
    p.id_proveedor,
    p.nombre AS proveedor,
    COUNT(pr.id_producto) AS cantidad_productos
FROM 
    Proveedores p
JOIN 
    Productos pr ON p.id_proveedor = pr.id_proveedor
GROUP BY 
    p.id_proveedor, p.nombre
HAVING 
    COUNT(pr.id_producto) > 5
ORDER BY 
    cantidad_productos DESC;
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