# ejercicios_msql
-- Ejercicio Total de ventas por cliente
    c.id_cliente,
    c.nombre AS cliente,
    COUNT(p.id_pedido) AS total_pedidos,
    SUM(dp.cantidad * hp.precio) AS monto_total
FROM 
    Clientes c
LEFT JOIN 
    Pedidos p ON c.id_cliente = p.id_cliente
LEFT JOIN 
    DetallesPedido dp ON p.id_pedido = dp.id_pedido
LEFT JOIN 
    HistoricoPrecios hp ON dp.id_precio_producto = hp.id_precio
GROUP BY 
    c.id_cliente, c.nombre
ORDER BY 
    monto_total DESC;
CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE Pedidos (
    id_pedido INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    total DECIMAL(10,2) NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);