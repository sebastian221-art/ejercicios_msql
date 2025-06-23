# ejercicios_msql
-- Ejercicio Cliente con mayor número de pedidos
SELECT 
    c.id_cliente,
    c.nombre,
    COUNT(p.id_pedido) AS total_pedidos
FROM 
    Clientes c
JOIN 
    Pedidos p ON c.id_cliente = p.id_cliente
GROUP BY 
    c.id_cliente, c.nombre
ORDER BY 
    total_pedidos DESC
LIMIT 1;
CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE Pedidos (
    id_pedido INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);