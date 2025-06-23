 ejercicios_msql
-- Ejercicio Pedidos y empleados que los gestionaron
SELECT 
    p.id_pedido,
    p.fecha_pedido,
    p.estado,
    c.nombre AS cliente,
    e.nombre AS empleado,
    pu.nombre_puesto AS puesto_empleado
FROM 
    Pedidos p
INNER JOIN 
    Clientes c ON p.id_cliente = c.id_cliente
INNER JOIN 
    Empleados e ON p.id_empleado = e.id_empleado
INNER JOIN 
    Puestos pu ON e.id_puesto = pu.id_puesto
ORDER BY 
    p.fecha_pedido DESC;
CREATE TABLE Empleados (
    id_empleado INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE Pedidos (
    id_pedido INT AUTO_INCREMENT PRIMARY KEY,
    id_empleado INT NOT NULL,
    FOREIGN KEY (id_empleado) REFERENCES Empleados(id_empleado)
);