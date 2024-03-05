# Software de Gestión para Videoclub

## Descripción

Este proyecto es un software de gestión para un videoclub que permite:

- Registrar socios con sus detalles personales y asignarles un número de socio.
- Registrar la dirección de correspondencia de los socios (opcional).
- Registrar películas con detalles como título, año de publicación, género, director y sinopsis.
- Registrar préstamos de películas a socios, incluyendo la fecha de préstamo y devolución.
- Este software está diseñado para ayudar a los videoclubs a gestionar eficientemente su inventario y préstamos, y a mejorar la experiencia de sus socios a través de recomendaciones personalizadas

Las consultas que se pueden realizar son:
- Consultar películas disponibles para alquilar.
- Determinar el género favorito de cada socio para recomendaciones de películas.

## Consideraciones

Se ha planteado que las películas pueden tener varios géneros y varios directores aunque en la base de datos actual no sea el caso.

## Tecnologías

El proyecto ha sido desarrollado utilizando **PostgreSQL** y **DBeaver**.

## Uso

Se puedo lanzar el script para que cree todas las tablas, relaciones y consultas, mostrando la última creada. Otra opción es ir seleccionando parte del código que se desea implementar.

## Lógica consultas

¿Películas que están disponibles para alquilar en este momento? 
Son todas las películas que hay, se genera vista "total_películas", menos las películas que están alquiladas "películas_alquiladas".
Se hace un left join con los campos que coinciden entre total_películas y peliculas_alquiladas, para que las que no están alquiladas queden vacías con campo null.

¿Cual es el género favorito de cada uno de mis socios para poder recomendarle películas cuando venga?
Se crea la vista peliculas_genero_socio donde se agrupa por socio, nombre y número de películas alquiladas por género. 
Creo la subconsulta max_genero para seleccionar por cada socio el género que más alquila.
Unifico las dos consultas peliculas_genero_socio y max_genero para obtener el resultado.

## Contribución

Este proyecto es de uso libre y cualquier contribución es bienvenida. Si deseas aportar más información o mejoras al proyecto, no dudes en hacerlo.

## Licencia

Este proyecto está bajo una licencia de uso libre.
