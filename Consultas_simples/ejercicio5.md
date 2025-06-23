# ejercicios_msql
-- Ejercicio Clientes sin dirección registrada
SELECT 
    c.id_cliente,
    c.nombre,
    c.email
FROM 
    Clientes c
LEFT JOIN 
    Ubicaciones u ON u.id_entidad = c.id_cliente 
    AND u.tipo_entidad = 'cliente'
WHERE 
    u.id_ubicacion IS NULL;
CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);

CREATE TABLE UbicacionCliente (
    id_ubicacion INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);