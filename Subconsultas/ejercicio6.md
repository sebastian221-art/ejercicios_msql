# ejercicios_msql
-- Ejercicio Cantidad total de pedidos por cliente y ciudad
SELECT 
    c.id_cliente,
    c.nombre AS cliente,
    u.ciudad,
    COUNT(p.id_pedido) AS total_pedidos
FROM 
    Clientes c
JOIN 
    Pedidos p ON c.id_cliente = p.id_cliente
JOIN 
    Ubicaciones u ON u.id_entidad = c.id_cliente 
    AND u.tipo_entidad = 'cliente'
    AND u.es_principal = TRUE
GROUP BY 
    c.id_cliente, c.nombre, u.ciudad
ORDER BY 
    total_pedidos DESC;
CREATE TABLE TiposClientes (
    id_tipo_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre_tipo VARCHAR(30) NOT NULL,
    descuento DECIMAL(5,2) NOT NULL
);
