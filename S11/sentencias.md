# Tarea TAS11 - views

## INVOICE_VIEW
## Visualizar la tabla invoice view antes de crear
- Sentencia:
```
SELECT i.id, i.code, i.created_at, i.total, c.fullname
FROM invoice i 
JOIN client c 
ON c.id= i.client_id;
```
- Captura:
<img src="./capturas/1S.png" alt="Captura de pantalla" width="500"/>

## Guardar el view de invoice para buscarlo solo con select

- Sentencia:
```
CREATE VIEW invoice_view AS
SELECT i.id, i.code, i.created_at, i.total, c.fullname
FROM invoice i 
JOIN client c 
```
- Captura:
<img src="./capturas/2S.png" alt="Captura de pantalla" width="500"/>


## Buscar con Select el invoice_view
- Sentencia:
```
SELECT * FROM invoice_view;
```
- Captura:
<img src="./capturas/3S.png" alt="Captura de pantalla" width="500"/>

## DETAIL_VIEW

## Visualizar el view de detail para buscarlo solo con select
- Sentencia:
```
SELECT d.id, d.quantity, p.description, d.price, d.quantity * p.price AS subtotal
FROM detail d JOIN product p
ON p.id = d.product_id;
```
- Captura:
<img src="./capturas/4S.png" alt="Captura de pantalla" width="500"/>

## Guardar el view de detail para buscarlo solo con select

- Sentencia:
```
CREATE VIEW detail_view AS
SELECT d.id, d.quantity, p.description, d.price, d.quantity * p.price AS subtotal
FROM detail d JOIN product p
ON p.id = d.product_id;
```
- Captura:
<img src="./capturas/5S.png" alt="Captura de pantalla" width="500"/>

## Buscar con Select el detail_view
- Sentencia:
```
SELECT * FROM detail_view;
```
- Captura:
<img src="./capturas/6S.png" alt="Captura de pantalla" width="500"/>
