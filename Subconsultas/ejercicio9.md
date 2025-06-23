# ejercicios_msql
-- Ejercicio Empleados que gestionan pedidos de proveedor específico
SELECT DISTINCT
    e.id_empleado,
    e.nombre AS empleado,
    pu.nombre_puesto AS puesto,
    pv.nombre AS proveedor
FROM 
    Empleados e
JOIN 
    Pedidos pe ON e.id_empleado = pe.id_empleado
JOIN 
    DetallesPedido dp ON pe.id_pedido = dp.id_pedido
JOIN 
    Productos pr ON dp.id_producto = pr.id_producto
JOIN 
    Proveedores pv ON pr.id_proveedor = pv.id_proveedor
JOIN 
    Puestos pu ON e.id_puesto = pu.id_puesto
WHERE 
    pv.id_proveedor = 5
ORDER BY 
    e.nombre;

CREATE TABLE HistorialPedidos (
    id_historial INT AUTO_INCREMENT PRIMARY KEY,
    id_pedido INT NOT NULL,
    fecha_cambio DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
    campo_afectado VARCHAR(50) NOT NULL,
    valor_anterior VARCHAR(255),
    valor_nuevo VARCHAR(255) NOT NULL,
    usuario_cambio VARCHAR(50) NOT NULL,
    FOREIGN KEY (id_pedido) REFERENCES Pedidos(id_pedido)
);