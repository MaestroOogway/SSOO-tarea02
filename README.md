# SSOO-tarea02  Autor:Fabián Alexis Vidal Torres  Correo:fabian.vidalt@alumnos.uv.cl

Para la resolucion del problema se utiliza bash en un entorno de Linux, primeramente se instala el componente "jq", puesto que se utilizara para generar el archivo solicitado, este componente permite efectuar la estructura de un json de manera adecuada. Dentro del script, mediante el comando "curl -s [url]" se obtienen los datos de la url especificada para luego trabajarlos, posteriormente mediante el uso de pipes se crea una estructura de json utilizando el componente anteriormente mencionado "jq" de la siguiente manera.

".[]|{payload: {items:[.[] | map(.) | .[] |{id:.id, item:.item_name}]}}"

Primero, se accede a la matriz original de la página,luego mediante el uso de "pipes" pasamos esa matriz a la estructura json que se desea crear.
Se itera sobre la matriz original recopilando todos los objetos que esta posee y luego con la función map creamos la nueva matriz con el contenido de cada objeto y la misma estructura que la matriz anterior.Todo se direcciona a un archivo json con redireccionamiento utilizando el metaracter ">".

Finalmente se ejecuta un condocional if-else en el script,el cual comprueba que el comando anteriormente hecho tenga su correspondiente fucionamiento, esto se hace con el uso de la variable $? la cual señala que si el valor de dicha variable es 0 , entonces no existen errores de ejecucion y posteriormente imprime el mensaje en pantalla de exito, de lo contrario reporta el error identificado.


Fuentes de información consultadas:
https://medium.com/@admin101/c%C3%B3mo-saber-si-el-%C3%BAltimo-comando-ingresado-se-ejecut%C3%B3-sin-errores-d04491770e3b
https://atareao.es/tutorial/scripts-en-bash/condicionales-en-bash/
https://www.baeldung.com/linux/jq-command-json
