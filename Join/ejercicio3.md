 ejercicios_msql
-- Ejercicio Pedidos y ubicaciones de clientes
SELECT 
    p.id_pedido,
    p.fecha_pedido,
    c.nombre AS cliente,
    u.direccion,
    u.ciudad,
    u.pais,
    u.codigo_postal
FROM 
    Pedidos p
LEFT JOIN 
    Clientes c ON p.id_cliente = c.id_cliente
LEFT JOIN 
    Ubicaciones u ON u.id_entidad = c.id_cliente 
    AND u.tipo_entidad = 'cliente'
    AND u.es_principal = TRUE
ORDER BY 
    p.fecha_pedido DESC;
CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE Ubicaciones (
    id_ubicacion INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    ciudad VARCHAR(50) NOT NULL,
    direccion TEXT NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);

CREATE TABLE Pedidos (
    id_pedido INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);