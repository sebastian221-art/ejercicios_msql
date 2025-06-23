# ejercicios_msql
-- Ejercicio Normalizar tabla Clientes
-- Tabla TiposClientes
CREATE TABLE TiposClientes (
    id_tipo_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre_tipo VARCHAR(30) NOT NULL,
    descuento DECIMAL(5,2) NOT NULL
);

-- Tabla Clientes normalizada
CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    id_tipo_cliente INT,
    FOREIGN KEY (id_tipo_cliente) REFERENCES TiposClientes(id_tipo_cliente)
);

-- Tabla DireccionesClientes
CREATE TABLE DireccionesClientes (
    id_direccion INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    direccion TEXT NOT NULL,
    ciudad VARCHAR(50) NOT NULL,
    pais VARCHAR(50) NOT NULL,
    codigo_postal VARCHAR(20) NOT NULL,
    es_principal BOOLEAN DEFAULT TRUE,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);