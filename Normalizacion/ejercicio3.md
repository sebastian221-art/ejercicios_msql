# ejercicios_msql
-- Ejercicio Separar tabla Empleados
-- Tabla Puestos
CREATE TABLE Puestos (
    id_puesto INT AUTO_INCREMENT PRIMARY KEY,
    nombre_puesto VARCHAR(50) NOT NULL,
    departamento VARCHAR(50) NOT NULL,
    salario_base DECIMAL(10,2) NOT NULL
);

-- Tabla Empleados normalizada
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