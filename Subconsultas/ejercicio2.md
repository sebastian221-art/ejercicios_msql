# ejercicios_msql
-- Ejercicio Mostrar ubicación de cada cliente en sus pedidos
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
JOIN 
    Clientes c ON p.id_cliente = c.id_cliente
JOIN 
    Ubicaciones u ON u.id_entidad = c.id_cliente 
    AND u.tipo_entidad = 'cliente'
    AND u.es_principal = TRUE
ORDER BY 
    p.fecha_pedido DESC;
CREATE TABLE Ubicaciones (
    id_ubicacion INT AUTO_INCREMENT PRIMARY KEY,
    tipo_entidad ENUM('cliente','proveedor','empleado','almacen','oficina') NOT NULL,
    id_entidad INT NOT NULL,
    direccion TEXT NOT NULL,
    ciudad VARCHAR(50) NOT NULL,
    provincia VARCHAR(50),
    pais VARCHAR(50) NOT NULL,
    codigo_postal VARCHAR(20),
    es_principal BOOLEAN DEFAULT FALSE
);