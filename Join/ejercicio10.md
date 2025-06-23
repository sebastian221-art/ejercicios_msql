 ejercicios_msql
-- Ejercicio Listado completo de inventario
SELECT 
    pr.id_producto,
    pr.nombre AS producto,
    pr.descripcion,
    pr.stock,
    pr.precio_actual,
    p.nombre AS proveedor,
    p.ruc,
    cp.nombre AS contacto_proveedor,
    cp.telefono AS telefono_proveedor,
    cat.nombre AS categoria,
    cat.ruta AS ruta_categoria
FROM 
    Productos pr
JOIN 
    Proveedores p ON pr.id_proveedor = p.id_proveedor
LEFT JOIN 
    ContactoProveedores cp ON p.id_proveedor = cp.id_proveedor AND cp.es_principal = TRUE
JOIN 
    CategoriasProductos cat ON pr.id_categoria = cat.id_categoria
ORDER BY 
    cat.nombre, pr.nombre;
CREATE TABLE Proveedores (
    id_proveedor INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE TiposProductos (
    id_tipo INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL
);

CREATE TABLE Productos (
    id_producto INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    id_proveedor INT NOT NULL,
    id_tipo INT NOT NULL,
    stock INT NOT NULL,
    precio DECIMAL(10,2) NOT NULL,
    FOREIGN KEY (id_proveedor) REFERENCES Proveedores(id_proveedor),
    FOREIGN KEY (id_tipo) REFERENCES TiposProductos(id_tipo)
);