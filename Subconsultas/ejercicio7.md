# ejercicios_msql
-- Ejercicio Clientes y proveedores en la misma ciudad
SELECT 
    c.nombre AS cliente,
    p.nombre AS proveedor,
    uc.ciudad
FROM 
    Clientes c
JOIN 
    Ubicaciones uc ON uc.id_entidad = c.id_cliente 
    AND uc.tipo_entidad = 'cliente'
JOIN 
    Proveedores p
JOIN 
    Ubicaciones up ON up.id_entidad = p.id_proveedor 
    AND up.tipo_entidad = 'proveedor'
WHERE 
    uc.ciudad = up.ciudad
ORDER BY 
    uc.ciudad, c.nombre;
    
CREATE TABLE TelefonosClientes (
    id_telefono INT AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT NOT NULL,
    numero VARCHAR(20) NOT NULL,
    tipo ENUM('casa','trabajo','movil','fax','otro') NOT NULL,
    es_principal BOOLEAN DEFAULT FALSE,
    notas VARCHAR(255),
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);