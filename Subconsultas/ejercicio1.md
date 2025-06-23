# ejercicios_msql
-- Ejercicio Listar todos los pedidos y el cliente asociado
SELECT 
    p.id_pedido,
    p.fecha_pedido,
    p.estado,
    c.id_cliente,
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
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    id_tipo_cliente INT,
    FOREIGN KEY (id_tipo_cliente) REFERENCES TiposClientes(id_tipo_cliente)
);

CREATE TABLE Pedidos (
    id_pedido INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    fecha_pedido DATETIME NOT NULL,
    estado ENUM('pendiente','procesando','enviado','entregado','cancelado') NOT NULL,
    id_empleado INT,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente),
    FOREIGN KEY (id_empleado) REFERENCES Empleados(id_empleado)
);