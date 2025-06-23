# ejercicios_msql
-- Ejercicio Listar productos con proveedor y tipo de producto
SELECT 
    pr.id_producto,
    pr.nombre AS producto,
    pr.descripcion,
    pr.precio_actual,
    p.nombre AS proveedor,
    cp.nombre AS categoria_producto,
    cp.ruta AS ruta_categoria
FROM 
    Productos pr
JOIN 
    Proveedores p ON pr.id_proveedor = p.id_proveedor
JOIN 
    CategoriasProductos cp ON pr.id_categoria = cp.id_categoria
ORDER BY 
    cp.nombre, pr.nombre;
CREATE TABLE Proveedores (
    id_proveedor INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    ruc VARCHAR(20),
    fecha_registro DATE NOT NULL
);

CREATE TABLE CategoriasProductos (
    id_categoria INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL,
    id_categoria_padre INT,
    nivel INT NOT NULL DEFAULT 1,
    FOREIGN KEY (id_categoria_padre) REFERENCES CategoriasProductos(id_categoria)
);

CREATE TABLE Productos (
    id_producto INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    descripcion TEXT,
    precio_actual DECIMAL(10,2) NOT NULL,
    stock INT NOT NULL DEFAULT 0,
    id_proveedor INT NOT NULL,
    id_categoria INT NOT NULL,
    FOREIGN KEY (id_proveedor) REFERENCES Proveedores(id_proveedor),
    FOREIGN KEY (id_categoria) REFERENCES CategoriasProductos(id_categoria)
);