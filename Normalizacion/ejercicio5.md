# ejercicios_msql
-- Ejercicio Normalizar Proveedores
-- Tabla Proveedores
CREATE TABLE Proveedores (
    id_proveedor INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    ruc VARCHAR(20),
    fecha_registro DATE NOT NULL
);

-- Tabla ContactoProveedores
CREATE TABLE ContactoProveedores (
    id_contacto INT AUTO_INCREMENT PRIMARY KEY,
    id_proveedor INT NOT NULL,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100),
    telefono VARCHAR(20),
    puesto VARCHAR(50),
    es_principal BOOLEAN DEFAULT TRUE,
    FOREIGN KEY (id_proveedor) REFERENCES Proveedores(id_proveedor)
);