# Tarea TAS9

## obtener la edad promedio de los miembros:
- Sentencia:
```
SELECT AVG(edad) AS edad_promedio FROM Miembros;
```
- Captura:
<img src="./capturas/1.0.png" alt="Captura de pantalla" width="500"/>

## obtener la edad mínima de los miembros:
- Sentencia:
```
SELECT MIN(edad) AS edad_minima FROM Miembros;
```
- Captura:
<img src="./capturas/2.0.png" alt="Captura de pantalla" width="500"/>

## obtener el número total de registros asistidos:
- Sentencia:
```
SELECT COUNT(*) AS total_registros_asistidos FROM Asistencias;
```
- Captura:
<img src="./capturas/3.0.png" alt="Captura de pantalla" width="500"/>

## obtener el número total de asistentes a todas las conferencias
- Sentencia:
```
SELECT COUNT(DISTINCT miembro_id) AS total_asistentes FROM Asistencias;
```
- Captura:
<img src="./capturas/4.0.png" alt="Captura de pantalla" width="500"/>

## obtener el número total de eventos por cada ciudad:
- Sentencia:
```
SELECT ciudad, COUNT(*) AS total_eventos 
FROM Conferencias 
GROUP BY ciudad;
```
- Captura:
<img src="./capturas/5.0.png" alt="Captura de pantalla" width="500"/>

## obtener el número de registros por cada miembro:
- Sentencia:
```
SELECT miembro_id, COUNT(*) AS total_registros 
FROM Asistencias 
GROUP BY miembro_id;
```
- Captura:
<img src="./capturas/6.0.png" alt="Captura de pantalla" width="500"/>

## obtener el número de registros por cada conferencia:
- Sentencia:
```
SELECT conferencia_id, COUNT(*) AS total_registros 
FROM Asistencias 
GROUP BY conferencia_id;
```
- Captura:
<img src="./capturas/7.0.png" alt="Captura de pantalla" width="500"/>