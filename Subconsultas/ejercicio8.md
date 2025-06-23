# ejercicios_msql
-- Ejercicio Total de ventas por tipo de producto
SELECT 
    cp.id_categoria,
    cp.nombre AS categoria,
    SUM(dp.cantidad) AS unidades_vendidas,
    SUM(dp.cantidad * hp.precio) AS ingreso_total
FROM 
    CategoriasProductos cp
JOIN 
    Productos p ON cp.id_categoria = p.id_categoria
JOIN 
    DetallesPedido dp ON p.id_producto = dp.id_producto
JOIN 
    HistoricoPrecios hp ON dp.id_precio_producto = hp.id_precio
GROUP BY 
    cp.id_categoria, cp.nombre
ORDER BY 
    ingreso_total DESC;
CREATE TABLE ContactoProveedores (
    id_contacto INT AUTO_INCREMENT PRIMARY KEY,
    id_proveedor INT NOT NULL,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100),
    telefono VARCHAR(20),
    puesto VARCHAR(50),
    es_principal BOOLEAN DEFAULT TRUE,
    FOREIGN KEY (id_proveedor) REFERENCES Proveedores(id_proveedor)
);