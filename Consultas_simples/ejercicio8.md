# ejercicios_msql
-- Ejercicio Tipos de productos disponibles
SELECT 
    id_categoria,
    nombre AS categoria,
    nivel,
    ruta
FROM 
    CategoriasProductos
ORDER BY 
    nivel, nombre;
CREATE TABLE TiposProductos (
    id_tipo INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL,
    descripcion TEXT
);