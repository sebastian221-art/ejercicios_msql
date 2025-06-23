# ejercicios_msql
-- Ejercicio Convertir UbicacionCliente en tabla genérica
CREATE TABLE Ubicaciones (
    id_ubicacion INT AUTO_INCREMENT PRIMARY KEY,
    tipo_entidad ENUM('cliente', 'proveedor', 'empleado', 'almacen', 'oficina') NOT NULL,
    id_entidad INT NOT NULL,
    tipo_direccion ENUM('fiscal', 'envio', 'personal', 'trabajo') NOT NULL,
    direccion TEXT NOT NULL,
    ciudad VARCHAR(50) NOT NULL,
    provincia VARCHAR(50),
    pais VARCHAR(50) NOT NULL,
    codigo_postal VARCHAR(20),
    coordenadas POINT SRID 4326,
    es_principal BOOLEAN DEFAULT FALSE,
    notas TEXT
);

CREATE INDEX idx_ubicacion_entidad ON Ubicaciones(tipo_entidad, id_entidad);
CREATE INDEX idx_ubicacion_principal ON Ubicaciones(tipo_entidad, id_entidad, es_principal);
CREATE SPATIAL INDEX idx_ubicacion_coordenadas ON Ubicaciones(coordenadas);