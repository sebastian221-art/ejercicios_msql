# ejercicios_msql
-- Ejercicio Relación muchos a muchos Empleados-Proveedores
CREATE TABLE EmpleadosProveedores (
    id_empleado INT NOT NULL,
    id_proveedor INT NOT NULL,
    fecha_asignacion DATE NOT NULL,
    rol ENUM('comprador', 'contacto', 'supervisor') NOT NULL,
    PRIMARY KEY (id_empleado, id_proveedor),
    FOREIGN KEY (id_empleado) REFERENCES Empleados(id_empleado),
    FOREIGN KEY (id_proveedor) REFERENCES Proveedores(id_proveedor)
);

CREATE INDEX idx_empleado_proveedor ON EmpleadosProveedores(id_empleado);
CREATE INDEX idx_proveedor_empleado ON EmpleadosProveedores(id_proveedor);