# ejercicios_msql
-- Ejercicio Los 5 productos más vendidos
SELECT 
    p.id_producto,
    p.nombre AS producto,
    SUM(dp.cantidad) AS total_vendido,
    SUM(dp.cantidad * hp.precio) AS ingreso_total
FROM 
    Productos p
JOIN 
    DetallesPedido dp ON p.id_producto = dp.id_producto
JOIN 
    HistoricoPrecios hp ON dp.id_precio_producto = hp.id_precio
GROUP BY 
    p.id_producto, p.nombre
ORDER BY 
    total_vendido DESC
LIMIT 5;
CREATE TABLE HistoricoPrecios (
    id_precio INT AUTO_INCREMENT PRIMARY KEY,
    id_producto INT NOT NULL,
    precio DECIMAL(10,2) NOT NULL,
    fecha_inicio DATE NOT NULL,
    fecha_fin DATE,
    FOREIGN KEY (id_producto) REFERENCES Productos(id_producto)
);

CREATE TABLE DetallesPedido (
    id_detalle INT AUTO_INCREMENT PRIMARY KEY,
    id_pedido INT NOT NULL,
    id_producto INT NOT NULL,
    cantidad INT NOT NULL,
    id_precio_producto INT NOT NULL,
    FOREIGN KEY (id_pedido) REFERENCES Pedidos(id_pedido),
    FOREIGN KEY (id_producto) REFERENCES Productos(id_producto),
    FOREIGN KEY (id_precio_producto) REFERENCES HistoricoPrecios(id_precio)
);