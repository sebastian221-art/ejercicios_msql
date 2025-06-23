# ejercicios_msql
-- Ejercicio Ingreso total por proveedor
SELECT 
    pv.id_proveedor,
    pv.nombre AS proveedor,
    COUNT(DISTINCT pe.id_pedido) AS pedidos_con_sus_productos,
    SUM(dp.cantidad) AS unidades_vendidas,
    SUM(dp.cantidad * hp.precio) AS ingreso_total
FROM 
    Proveedores pv
JOIN 
    Productos pr ON pv.id_proveedor = pr.id_proveedor
JOIN 
    DetallesPedido dp ON pr.id_producto = dp.id_producto
JOIN 
    HistoricoPrecios hp ON dp.id_precio_producto = hp.id_precio
JOIN 
    Pedidos pe ON dp.id_pedido = pe.id_pedido
GROUP BY 
    pv.id_proveedor, pv.nombre
ORDER BY 
    ingreso_total DESC;

CREATE TABLE EmpleadosProveedores (
    id_empleado INT NOT NULL,
    id_proveedor INT NOT NULL,
    fecha_asignacion DATE NOT NULL,
    rol ENUM('comprador','contacto','supervisor') NOT NULL,
    PRIMARY KEY (id_empleado, id_proveedor),
    FOREIGN KEY (id_empleado) REFERENCES Empleados(id_empleado),
    FOREIGN KEY (id_proveedor) REFERENCES Proveedores(id_proveedor)
);