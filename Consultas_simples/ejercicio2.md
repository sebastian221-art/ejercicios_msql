# ejercicios_msql
-- Ejercicio Clientes en una ciudad específica
SELECT 
    c.id_cliente,
    c.nombre,
    c.email,
    u.ciudad,
    u.direccion
FROM 
    Clientes c
JOIN 
    Ubicaciones u ON u.id_entidad = c.id_cliente 
    AND u.tipo_entidad = 'cliente'
WHERE 
    u.ciudad = 'Madrid'
ORDER BY 
    c.nombre;
CREATE TABLE Clientes (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100)
);

CREATE TABLE UbicacionCliente (
    id_ubicacion INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    ciudad VARCHAR(50) NOT NULL,
    direccion TEXT NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);