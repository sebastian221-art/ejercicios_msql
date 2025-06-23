 ejercicios_msql
-- Ejercicio Total de pedidos por ubicación de cliente
SELECT 
    u.ciudad,
    u.pais,
    COUNT(p.id_pedido) AS total_pedidos,
    SUM(dp.cantidad * hp.precio) AS monto_total
FROM 
    Ubicaciones u
JOIN 
    Clientes c ON u.id_entidad = c.id_cliente AND u.tipo_entidad = 'cliente'
JOIN 
    Pedidos p ON c.id_cliente = p.id_cliente
JOIN 
    DetallesPedido dp ON p.id_pedido = dp.id_pedido
JOIN 
    HistoricoPrecios hp ON dp.id_precio_producto = hp.id_precio
GROUP BY 
    u.ciudad, u.pais
ORDER BY 
    total_pedidos DESC;
CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE Ubicaciones (
    id_ubicacion INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    ciudad VARCHAR(50) NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);

CREATE TABLE Pedidos (
    id_pedido INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);