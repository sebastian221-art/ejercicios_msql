 ejercicios_msql
-- Ejercicio Tipos de producto y productos asociados
SELECT 
    t.id_categoria,
    t.nombre AS categoria,
    p.id_producto,
    p.nombre AS producto,
    p.descripcion,
    p.precio_actual
FROM 
    CategoriasProductos t
INNER JOIN 
    Productos p ON t.id_categoria = p.id_categoria
ORDER BY 
    t.nombre, p.nombre;
CREATE TABLE TiposProductos (
    id_tipo INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL
);

CREATE TABLE Productos (
    id_producto INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    id_tipo INT NOT NULL,
    FOREIGN KEY (id_tipo) REFERENCES TiposProductos(id_tipo)
);