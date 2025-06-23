 ejercicios_msql
-- Ejercicio Clientes y número de pedidos
SELECT 
    c.id_cliente,
    c.nombre,
    c.email,
    COUNT(p.id_pedido) AS total_pedidos
FROM 
    Clientes c
LEFT JOIN 
    Pedidos p ON c.id_cliente = p.id_cliente
GROUP BY 
    c.id_cliente, c.nombre, c.email
ORDER BY 
    total_pedidos DESC;
CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE Pedidos (
    id_pedido INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);