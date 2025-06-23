# ejercicios_msql
-- Ejercicio Empleados que gestionan pedidos en ciudad específica
SELECT DISTINCT
    e.id_empleado,
    e.nombre AS empleado,
    pu.nombre_puesto AS puesto,
    u.ciudad
FROM 
    Empleados e
JOIN 
    Pedidos p ON e.id_empleado = p.id_empleado
JOIN 
    Clientes c ON p.id_cliente = c.id_cliente
JOIN 
    Ubicaciones u ON u.id_entidad = c.id_cliente 
    AND u.tipo_entidad = 'cliente'
JOIN 
    Puestos pu ON e.id_puesto = pu.id_puesto
WHERE 
    u.ciudad = 'Barcelona'
ORDER BY 
    e.nombre;
CREATE TABLE Puestos (
    id_puesto INT AUTO_INCREMENT PRIMARY KEY,
    nombre_puesto VARCHAR(50) NOT NULL,
    departamento VARCHAR(50) NOT NULL,
    salario_base DECIMAL(10,2) NOT NULL
);

CREATE TABLE Empleados (
    id_empleado INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    fecha_contratacion DATE NOT NULL,
    id_puesto INT NOT NULL,
    salario_actual DECIMAL(10,2) NOT NULL,
    jefe_directo INT,
    FOREIGN KEY (id_puesto) REFERENCES Puestos(id_puesto),
    FOREIGN KEY (jefe_directo) REFERENCES Empleados(id_empleado)
);