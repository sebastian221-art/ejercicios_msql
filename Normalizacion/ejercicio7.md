# ejercicios_msql
-- Ejercicio Transformar TiposProductos en jerárquica
CREATE TABLE CategoriasProductos (
    id_categoria INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL,
    id_categoria_padre INT,
    nivel INT NOT NULL DEFAULT 1,
    ruta VARCHAR(255),
    FOREIGN KEY (id_categoria_padre) REFERENCES CategoriasProductos(id_categoria)
);

DELIMITER //
CREATE TRIGGER tr_categoria_before_insert
BEFORE INSERT ON CategoriasProductos
FOR EACH ROW
BEGIN
    IF NEW.id_categoria_padre IS NOT NULL THEN
        SET NEW.nivel = (SELECT nivel FROM CategoriasProductos WHERE id_categoria = NEW.id_categoria_padre) + 1;
    END IF;
END//
DELIMITER ;