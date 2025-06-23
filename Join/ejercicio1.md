# ejercicios_msql
-- Ejercicio Pedidos con nombres de clientes
SELECT 
    p.id_pedido,
    p.fecha_pedido,
    p.estado,
    c.nombre AS nombre_cliente,
    c.email AS email_cliente
FROM 
    Pedidos p
INNER JOIN 
    Clientes c ON p.id_cliente = c.id_cliente
ORDER BY 
    p.fecha_pedido DESC;

CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE Pedidos (
    id_pedido INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    fecha_pedido DATETIME NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);
