 ejercicios_msql
-- Ejercicio Empleados y sus pedidos
SELECT 
    e.id_empleado,
    e.nombre AS empleado,
    p.id_pedido,
    p.fecha_pedido,
    p.estado
FROM 
    Empleados e
LEFT JOIN 
    Pedidos p ON e.id_empleado = p.id_empleado
ORDER BY 
    e.nombre, p.fecha_pedido DESC;
CREATE TABLE Empleados (
    id_empleado INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE Pedidos (
    id_pedido INT AUTO_INCREMENT PRIMARY KEY,
    id_empleado INT,
    FOREIGN KEY (id_empleado) REFERENCES Empleados(id_empleado)
);