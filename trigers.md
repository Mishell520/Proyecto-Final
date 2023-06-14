# Proyecto-Final
Proyecto final Analisis en Sistemas Grupo 2 

DELIMITER //

CREATE TRIGGER descuento_stock
AFTER INSERT ON detalle_venta
FOR EACH ROW
BEGIN
  -- Actualizar el stock del producto en base a la cantidad comprada
  UPDATE productos
  SET stock = stock - NEW.cantidad
  WHERE id = NEW.producto_id;
END//

DELIMITER ;

DELIMITER //

CREATE TRIGGER descuento_stock
AFTER INSERT ON detalle_compra
FOR EACH ROW
BEGIN
  -- Actualizar el stock del producto en base a la cantidad comprada
  UPDATE productos
  SET stock = stock + NEW.cantidad
  WHERE id = NEW.producto_id;
END//

DELIMITER ;
