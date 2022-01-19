# Práctica 1 - Calculadora HTTP

En la URL http://malamen.dit.upm.es/calc hay desplegada una calculadora HTTP que sirve para sumar, restar, dividir y multiplicar dos números, obteniendo el resultado en formato JSON.

Para usar esta calculadora debe enviarse una petición HTTP de tipo POST a la URL anterior, y pasar en el cuerpo (body) los dos números y el operador que se quieran aplicar.

Debe usarse para el body el mismo formato que se usa en un formulario.
El tipo de contenido debe ser `Content-type: application/x-www-form-urlencoded`, los operandos deben asignarse a las variables n1 y n2, el operador a la variable op, todo separado con "&", y usando escapado URL.

Así, para suma 3 y 4, hay que pasar en el body la siguiente cadena:

n1=3&n2=4&op=%2B

Algunos operadores han de ser escapados (transformados para su uso en URL).
Para escapar el operador suma debe usarse la codificación %2B, y para la multiplicación %2F.

La petición HTTP debe incluir también otras cabeceras, como por ejemplo:

Host: direccion del servidor
Accept: text/html,text/text,application/json
Connection: keep-alive para no cerrar la conexión
Content-Length: tamaño del body

La respuesta HTTP que devuelve el servidor es un objeto JSON que puede contener el resultado pedido, o un error si hay algún problema.

Se pide escribir varios ficheros con peticiones al servidor, siguiendo las siguientes especificaciones:

* `suma.txt`, una petición para sumar los valores `3` y `4`.
* `error400.txt`, una petición inválida, que causa que el servidor devuelva un error 400.
* `incompleta.txt`, una petición que causa que el servidor "quede a la espera de más datos", causando un timeout después de un tiempo.


# Comprobar las peticiones

Puede probar 

## En *nix (GNU/Linux, Mac, BSD)

(También válido en la bash shell de Windows o en WSL (Windows Subsystem for Linux))

Lanzar el siguiente comando:

```shell
nc malamen.dit.upm.es 80 < peticion.txt
```

Este comando escribirá en pantalla la respuesta HTTP recibida, y en su body debe llegar un objeto JSON indicando el resultado.

En Windows:

#TODO
... #USAR LINUX# ...


# TODO

* Retocar el enunciado
* Modificar CourseID y detalles del package.json para alinearlo con la tarea de Moodle
* Añadir instrucciones netcat Windows
* ¿Especificar la puntuación?
* He añadido 3 queries diferentes. Originalmente sólo había una (la suma). Hay que decidir si dejar sólo eso.
* Se podría hacer que la query de cada usuario dependa de su correo electrónico (p.e., sumar el número de vocales y el de consonantes), así cada alumno tiene un trabajo diferente.
