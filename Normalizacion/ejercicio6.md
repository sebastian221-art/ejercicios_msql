# ejercicios_msql
-- Ejercicio Crear tabla de Teléfonos
CREATE TABLE TelefonosClientes (
    id_telefono INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    numero VARCHAR(20) NOT NULL,
    tipo ENUM('casa', 'trabajo', 'movil', 'fax', 'otro') NOT NULL,
    es_principal BOOLEAN DEFAULT FALSE,
    notas VARCHAR(255),
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);

CREATE INDEX idx_telefono_cliente ON TelefonosClientes(id_cliente);