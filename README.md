Actividad - Semana 6
Objetivos
El objetivo de esta actividad es familiarizaros con los conceptos básicos de la programación de la shell BASH. En concreto con los temas abordados hasta la semana 6 de prácticas.

Tareas
Te proponemos que realices las siguiente tareas para la próxima semana:

1. Leer los contenidos de la Lección de la semana 6
En el aula podrás encontrar un enlace al documento Configuración del entorno, creación del primer script y control de flujo. Te sugerimos que lo leas y hagas los ejemplos que allí se proponen por ti mismo. Si quieres ampliar conocimientos también dispones de la presentación BASH Scripting: Una introducción mediante ejemplos.

Al termina esta tarea anterior debes tener tu propio script sysinfo_page a medio hacer. ¿Serías capaz de hacer lo siguiente?

2. Implementar el código de la función drives_space()
Modificar la función drive_space() para mostrar el espacio ocupado en las particiones/discos duros del sistema sabiendo que el comando df ya proporciona esa información. Observa detenidamente el ejemplo de show_uptime donde se ve como se usan las etiquetas <pre></pre> para preservar los saltos de línea introducidos por el comando uptime a la hora de mostrar el HTML.

3. Implementar el código de la función home_space()
Modificar la función home_space() para mostrar el espacio ocupado por cada directorio personal en /home teniendo presente que:

Si el usuario que ejecuta el script es root, debe mostrar es espacio ocupado por cada directorio personal en /home.
Si el usuario que ejecuta el script NO es root, debe mostrar el espacio ocupado por el directorio personal del usuario actual. Recuerden que la variable de entorno $USER nos indica el nombre del usuario actual.
Debes usar el comando du, que recorre los directorios indicados como argumento (p. ej. du /home/jmtorres /home/jttoledo o du /home/b*) mostrando el espacio ocupado por los archivos de cada subdirectorio de su interior así como el total. Te recomendamos que pruebes el comando para que te familiarices con él.
Como sólo interesa la suma total del espacio ocupado por cada directorio de usuario hay que buscar en la ayuda (o en man du) la opción que solo muestra estos totales (en nuestro ejemplo, el total de lo ocupado por /home/jmtorres y por /home/jttoledo).
La lista proporcionada por du debe mostrarse ordenada en orden decreciente (primero el directorio que ocupa más espacio).
4. Evaluación
El script realizado se subirá en cualquier momento a esta tarea, desde la fecha actual hasta el día de la próxima sesión práctica.
Esta actividad por si misma no puntuará para la calificación final.
Se calificará por la correcta realización de los cambios al script que los profesores propongan durante la próxima sesión práctica. Por lo tanto es importante llegar a la misma con esta actividad ya hecha.



Actividad - Semana 7
Objetivos
El objetivo de esta actividad es familiarizaros con los conceptos básicos de la programación de la shell BASH. En concreto con los temas abordados hasta la semana 7 de prácticas.

Tareas
Te proponemos que realices las siguiente tareas para la próxima semana:

1. Leer los contenidos de la Lección de la semana 7
En el aula podrás encontrar un enlace al documento Control de flujo, parámetros posicionales y entrada estándar. Te sugerimos que lo leas y hagas los ejemplos que allí se proponen por ti mismo. Te recordamos que también dispones de la presentación BASH Scripting: Una introducción mediante ejemplos.

Al terminar conocerás algunos nuevos elementos de la programación en BASH y será la hora de utilizarlos en tu script sysinfo_page a medio hacer.

2. Incorporar el procesamiento de la línea de comandos
Modificar el programa principal del script para incorporar el código de procesamiento de la línea de comandos usado como ejemplo en el apartado Opciones de la línea de comandos de los apuntes de esta semana.

Es importante tener en cuenta que ahora la salida en HTML debe volcarse al archivo indicado en la variable $filename. ¿Sabrías hacerlo? Sólo tienes que crear una función a modo de subcomando que contenga la sentencia del comando cat con el script-aquí (<< _EOF_...). Ahora desde el programa principal puedes invocar dicha función redirigiendo su contenido a lo indicado en la variable $filename.

3. Implementar el modo interactivo
Implementa en el programa principal del script el modo interactivo:

Debe ejecutarse sólo cuando $interactive es 1, obviamente después de procesar la línea de comandos
Debe preguntar al usuario por el nombre del archivo de salida.
Debe comprobar si el archivo ya existe. Si así es, debe indicar al usuario lo que ocurre y preguntarle si quiere sobreescribirlo. En caso negativo el script debe terminar.
Si el script no termina, el nombre del archivo de salida debe acabar almacenado en la variable $filename para su uso posterior por parte del script.
4. Nueva opción de la línea de comandos: filtrado de particiones
Imagina que el usuario está interesado en controlar que particiones se muestran al calcular el espacio libre en disco en la función drive_space. Así que vamos a añadir la opción "-p, --partitions-filter" con la que filtrar las particiones o unidades de disco mediante expresiones regulares.

Incorporar al código que procesa los argumentos de la línea de comando la opción "-p, --partitions-filter". Esta opción recibirá un argumento que será la expresión regular con la que filtrar las particiones mostradas con df, de tal forma que sólo se muestren aquellas que cumplan con lo indicado por el filtro. Es decir, nuestro script se podría invocar de la siguiente manera: sysinfo_page -p "sd*" o sysinfo_page --partitions-filter "sd*".
Sabiendo que las funciones se invocan como comandos y reciben sus argumentos a través de parámetros posicionales, como ocurre con el script principal:
param() {
    echo '$1 =' $1
    echo '$2 =' $2
}
param palabra1 palabra2

pasar el filtro especificado por el usuario a la función drive_space.
Modificar la función drive_space para que si el usuario especificó un filtro mediante una expresión regular, la salida del comando df se filtre desde la primera columna usando grep con dicha expresión. Si no es especificó ninguna, debería mostrarse la salida de df en crudo, sin aplicar ningún filtro.
A aquellos que tengan más interés les proponemos un reto adicional. Al filtrar, con mucha probabilidad desaparecerá el encabezado de la salida del comando df. ¿Serías capaz de evitarlo haciendo que el encabezado saliera siempre independientemente del filtro indicado por el usuario?

5. Evaluación
El script realizado se subirá en cualquier momento a esta tarea, desde la fecha actual hasta el día de la próxima sesión práctica.
Esta actividad por si misma no puntuará para la calificación final.
Se calificará por la correcta realización de los cambios al script que los profesores propongan durante la próxima sesión práctica. Por lo tanto es importante llegar a la misma con esta actividad ya hecha.

Actividad - Semana 8
Objetivos
El objetivo de esta actividad es familiarizaros con los conceptos básicos de la programación de la shell BASH. En concreto con los temas abordados hasta la semana 8 de prácticas.

Tareas
Te proponemos que realices las siguiente tareas para la próxima semana:

1. Leer los contenidos de la Lección de la semana 8
En el aula podrás encontrar un enlace al documento Manejo de errores, depuración y comandos adicionales. Te sugerimos que lo leas y hagas los ejemplos que allí se proponen por ti mismo. Te recordamos que también dispones de la presentación BASH Scripting: Una introducción mediante ejemplos.

Al terminar conocerás algunos nuevos elementos de la programación en BASH y será la hora de utilizarlos en tu script sysinfo_page a medio hacer.

2. Mejorar el procesamiento de errores
Incorpora a tu script la función de salida con error error_exit. Úsala para salir con error si se pasa al script una opción no soportada, después de mostrar la ayuda sobre el uso del programa de la función usage. 

Además, antes de procesar la línea de comandos comprobar si los comandos df, du y uptime existen. Si no es así salir con un error indicando que falta un programa básico para el funcionamiento del script. La ruta del archivo que implementa un comando se puede obtener ejecutando which uptime, por ejemplo. Mientras que el comando test dispone de una opción para comprobar si el archivo indicado existe y es ejecutable.

3. Mejorar home_space()
Vamos a mejorar nuestra función home_space con algunas funciones adicionales.

Si el usuario actual es el root, procesaremos cada directorio en /home.
Mientras que si el usuario actual no es root, procesaremos sólo el directorio personal del usuario.
Para cada directorio a procesar usaremos du y find para calcular:

El espacio total usado, como hasta ahora.
El número total de archivos en el directorio y los subdirectorios de éste.
El número total de subdirectorios en éste.
Mostrar un cabecera como la siguiente:

Directorios Archivos Usado Directorio

y a continuación una línea para cada directorio procesado con el número de directorios, el número de archivos, el espacio total usado y la ruta del directorio.

¿Sabrías alinear las columnas usando printf para imprimir la información?

4. Desarrollar open_files()
El comando lsof se utiliza para listar todos los archivos abiertos en el sistema. El comando es complejo y admite diversas opciones. Una de las más interesantes es -u, que permite conocer todos los archivos abiertos por un usuario concreto:

$ lsof -u root

Incorpora a tu script sysinfo_page una función open_files que muestre una lista ordenada y sin duplicados de usuarios que tienen algún archivo abierto junto con el número de dichos archivos abiertos por cada usuario. Es decir, algo como esto:

<h2>Número de archivos abiertos</h2>
<pre>
Usuario    Nº Archivos
jmtorres   18
jttoledo   25
</pre>
NOTA: El comando tail +n te permite eliminar las primeras n líneas de la entrada ¿para qué lo podrías usar?

6. Revisa y organiza tu script

En este punto podemos dar por terminado el desarrollo del script sysinfo_page. Revisa tu código y límpialo para asegurarte que tiene suficiente calidad como para que se note que es de un buen desarrollador:

Recuerda facilitar la lectura de tu código:
Usa comentarios en los elementos más complejos del programa para que te sea más sencillo entenderlo cuando haya pasado un tiempo y no te acuerdes
Usa funciones para compartimentar el programa, así como variables y constantes (variables en mayúsculas) que hagan tu código más legible.
Incluye código para procesar la línea de comandos.
Se debe mostrar ayuda sobre el uso y las opciones que soporta si el usuario emplea la opción -h o --help.
Se debe indicar el error y mostrar ayuda sobre el uso si el usuario emplea uno opción no soportada
Ojo con la sustitución de variables y las comillas. En caso de problemas piensa en cómo quedarían las sentencias si las variables no valieran nada ¿tendría sentido para BASH el comando a ejecutar?
Maneja adecuadamente los errores.
En caso de error muestra un mensaje y sal con código de salida distinto de 0. Recuerda la función error_exit que hemos desarrollado y úsala donde haga falta.
Trata como un error que el usuario emplee opciones no soportadas
Detecta si los comandos de los que depende tus script, como lsof, están instalados antes de usarlo. Si no lo está, indica el error.
Haz lo mismo con las otras posibles condiciones de error que se te ocurran ¿has probado a invocar tu programa opciones absurdas a ver si lo haces fallar?
5. Evaluación

El script realizado se subirá en cualquier momento a esta tarea, desde la fecha actual hasta el día de la próxima sesión práctica.
Esta actividad por si misma no puntuará para la calificación final.
Se calificará por la correcta realización de los cambios al script que los profesores propongan durante la próxima sesión práctica. Por lo tanto es importante llegar a la misma con esta actividad ya hecha.


Práctica de BASH - proc
Objetivos
Demostrar al mundo que ya somos unos expertos en el desarrollo de scripts de BASH guiño

Nuestro propio comando ps
¿Alguna vez te has preguntado de donde saca el comando ps la información acerca de los procesos en el sistema? La respuesta es muy sencilla, del directorio /proc.

Entra en el directorio /proc y obsérvalo un momento. Verás muchas cosas pero lo más interesante es que cada directorio /proc/<numero> representa a un proceso donde <numero> es el PID de dicho proceso. Del contenido de los archivos de cada directorio podemos obtener toda la información que necesitamos:

/proc/<pid>/cmdline la línea de comandos con la que se ejecutó el programa.
/proc/<pid>/cwd es un enlace al directorio actual de trabajo del proceso (para obtener la dirección a la que apunta un enlace simbólico se puede usar el comando readlink <ruta_del_enlace>)
/proc/<pid>/status permite obtener
El PPID (PID del proceso padre) 
UID y GID del proceso. Se muestra por columnas. La primera es el UID/GID real y la segunda el UID/GID efectivo.
Estado (state)
Número de hilos (Threads)
etc. (ver http://linux.die.net/man/5/proc)
Tareas
Te proponemos que realices un script que al menos incluya las siguientes funcionalidades:

1. Listado de procesos
Usando lo aprendido hasta el momento en clase desarrolla el script 'myps' que, si no se especifica opción, muestre una lista de todos los procesos del sistema:

Crea una función para extraer cada unidad de información de un proceso a partir del PID:
Por ejemplo, una función get_cmdline que reciba el PID e imprima la línea de comandos:
get_cmdline 805
/usr/bin/kate
O una función get_user que reciba el PID e imprima el nombre de usuario:
get_user 805
jmtorres
Recuerda que /proc/pid/status sólo te da el UID, así que debes buscar en /etc/passwd el nombre de usuario que corresponde a ese UID.
O una función get_cmd que reciba el PID e imprima el directorio actual de trabajo:
get_cwd 805
/home/jmtorres
Y así para toda la información que haya que mostrar en estra práctica...
Imprime una tabla con proceso por fila y para cada uno muestra:
PID PPID usuario grupo estado "nº de hilos" "Directorio de trabajo" "Línea de comandos"
Recuerda usar printf o column para que las columnas queden correctamente alienadas.
Maneja adecuadamente los errores.
Si el script no se ejecuta como root, es posible que no tengamos permisos para abrir alguno de los archivos y, por tanto, para recuperar cierta información. Evita mensajes de error en ese caso, detectando la condición antes de provocarla y usando las comillas adecuadamente para devolver y usar cadenas vacías en las columnas.
En caso de error grave muestra un mensaje y sal con código de salida distinto de 0. Recuerda la función error_exit de ejercicios anteriores y, si lo crees conveniente, reúsala o haz la tuya propia.
Trata como un error que el usuario emplee opciones no soportadas
Haz lo mismo con las otras posibles condiciones de error que se te ocurran ¿has probado a invocar tu programa opciones absurdas a ver si lo haces fallar?
Recuerda facilitar la lectura de tu código:
Usa comentarios en los elementos más complejos del programa para que te sea más sencillo entenderlo cuando haya pasado un tiempo y no te acuerdes
Usa funciones para compartimentar el programa, así como variables y constantes (variables en mayúsculas) que hagan tu código más legible.
Incluye código para procesar la línea de comandos.
Se debe mostrar ayuda sobre el uso si el usuario emplea la opción -h o --help.
Se debe indicar el error y mostrar ayuda sobre el uso si el usuario emplea uno opción no soportada
Ojo con la sustitución de variables y las comillas. En caso de problemas piensa en cómo quedarían las sentencias si las variables no valieran nada ¿tendría sentido para BASH el comando a ejecutar?
2. Buscar un proceso por el nombre de comando
Crea una función a la que pasar la línea de comandos del proceso (el contenido de /proc/pid/cmdline) y que prima sólo el nombre del comando, sin ruta ni opciones. Para eso recuerda el comando basename.
Añade la opción '-n comando' de tal forma que sólo se muestren aquellos procesos que ejecuten el programa del comando 'comando'. Recuerda que en el paso anterior escribiste una función que te será muy útil.
Añade la opción '-p pid' de tal forma que sólo muestre el proceso con el PID indicado.
Ambas opciones son excluyentes. Si se indican las dos hay, que indicar el error al usuario.
Si se usan las opciones -n o -p, después de imprimir la línea de información de cada proceso hay que mostrar información adicional antes de imprimir la siguiente línea: estadísticas de operaciones de entrada/salida extraídas de /proc/pid/io, los límites configurados para el proceso (/proc/pid/limits) y cualquier otra cosa que te llame la atención...
Evaluación
El script realizado se subirá en cualquier momento a esta tarea, desde la fecha actual hasta el día de la próxima sesión práctica.
Esta actividad se calificará por la correcta realización de los cambios al script que los profesores propongan durante la próxima sesión práctica (la de la semana del 24 al 28 de noviembre). Por lo tanto es importante llegar a la misma con esta actividad ya hecha.
El trabajo bien hecho al desarrollar esta actividad y el grado de ajuste a los requisitos establecidos, modulará la nota final de la actividad siempre que los profesores la valores como correcta, por la realización de los cambios propuestos comentados en el punto anterior.