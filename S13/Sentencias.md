# Tarea TAS13 

## triggers
## Crear un función y un trigger para validar que el numero de cedula del cliente tenga 10 números (no letras) en la tabla cliente.
- Sentencia:
```
CREATE OR REPLACE FUNCTION validate_cedula() RETURNS TRIGGER AS $$
BEGIN
    IF NOT (NEW.cedula ~ '^\d{10}$') THEN
        RAISE EXCEPTION 'La cédula debe tener 10 números';
    END IF;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER validate_cedula_trigger
BEFORE INSERT OR UPDATE ON client
FOR EACH ROW
EXECUTE FUNCTION validate_cedula();;
```


## Crear un función y un trigger para que cada vez que se inserte un nuevo registro en la tabla item se disminuya el stock de la tabla product.

- Sentencia:
```
CREATE OR REPLACE FUNCTION decrease_stock() RETURNS TRIGGER AS $$
BEGIN
    UPDATE product
    SET stock = stock - NEW.quantity
    WHERE product_id = NEW.product_id;

    IF (SELECT stock FROM product WHERE product_id = NEW.product_id) < 0 THEN
        RAISE EXCEPTION 'No hay suficiente stock para el producto';
    END IF;

    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER decrease_stock_trigger
AFTER INSERT ON item
FOR EACH ROW
EXECUTE FUNCTION decrease_stock();
```


## Crear un función y un trigger para la tabla invoice donde valide que el campo create_at sea del año actual (fecha sistema).


- Sentencia:
```
CREATE OR REPLACE FUNCTION validate_invoice_date() RETURNS TRIGGER AS $$
BEGIN
    IF EXTRACT(YEAR FROM NEW.create_at) <> EXTRACT(YEAR FROM CURRENT_DATE) THEN
        RAISE EXCEPTION 'La fecha de creación debe ser del año actual';
    END IF;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER validate_invoice_date_trigger
BEFORE INSERT OR UPDATE ON invoice
FOR EACH ROW
EXECUTE FUNCTION validate_invoice_date();
```


## Crear un función y un trigger para la tabla client y validar que el correo tenga un @.
- Sentencia:
```
CREATE OR REPLACE FUNCTION validate_email() RETURNS TRIGGER AS $$
BEGIN
    IF POSITION('@' IN NEW.email) = 0 THEN
        RAISE EXCEPTION 'El correo debe contener un @';
    END IF;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER validate_email_trigger
BEFORE INSERT OR UPDATE ON client
FOR EACH ROW
EXECUTE FUNCTION validate_email();
```
