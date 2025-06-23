 ejercicios_msql
-- Ejercicio Productos no pedidos
SELECT 
    p.id_producto,
    p.nombre AS producto,
    p.descripcion
FROM 
    DetallesPedido dp
RIGHT JOIN 
    Productos p ON dp.id_producto = p.id_producto
WHERE 
    dp.id_producto IS NULL
ORDER BY 
    p.nombre;
CREATE TABLE Productos (
    id_producto INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE DetallesPedido (
    id_detalle INT AUTO_INCREMENT PRIMARY KEY,
    id_producto INT,
    id_pedido INT NOT NULL,
    FOREIGN KEY (id_producto) REFERENCES Productos(id_producto)
);