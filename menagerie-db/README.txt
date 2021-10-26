Este directorio contiene archivos que se pueden usar para configurar la colección de animales
base de datos que se utiliza en el capítulo tutorial de la Referencia de MySQL
Manual.

Estas instrucciones asumen que su directorio de trabajo actual es
el directorio que contiene los archivos creados al descomprimir el
distribución menagerie.zip o menagerie.tar.gz. Cualquier programa MySQL
que utiliza (como mysql o mysqlimport) debe invocarse desde
ese directorio.

Para invocar mysql o mysqlimport, especifique el nombre completo de la ruta
al programa, o establezca su variable de entorno PATH en el contenedor
directorio que contiene los programas para que pueda invocarlos
desde cualquier lugar sin especificar su nombre de ruta completo. (Ver su
instrucciones de ayuda del sistema operativo para las variables de entorno).
El nombre de la ruta completa a los programas depende de dónde esté instalado MySQL.

Para los comandos mysql y mysqlimport, proporcione los parámetros de conexión
necesario (host, usuario, contraseña) en la línea de comando antes de la base de datos
nombre. Para más información, ver:

  http://dev.mysql.com/doc/mysql/en/invoking-programs.html


Primero, debe crear la base de datos de la colección de animales. Invoque el programa mysql,
y luego emita esta declaración:

  mysql> CREATE DATABASE menagerie;

Si usa un nombre de base de datos diferente del menagerie en CREATE
Declaración de BASE DE DATOS, use el mismo nombre dondequiera que vea colección de animales
en las siguientes instrucciones.

Select the menagerie database as the default database:

  mysql> USE menagerie;

Create the pet table:

  mysql> SOURCE cr_pet_tbl.sql

Load the pet table:

  mysql> LOAD DATA LOCAL INFILE 'pet.txt' INTO TABLE pet;

To add Puffball's record, use this command:

  mysql> SOURCE ins_puff_rec.sql

Create the event table:

  mysql> SOURCE cr_event_tbl.sql

Load the event table:

  mysql> LOAD DATA LOCAL INFILE 'event.txt' INTO TABLE event;

Procedimiento alternativo:

Si desea crear y cargar las tablas desde su intérprete de comandos
(cmd.exe o command.com en Windows, o su shell en Unix), use el
siguientes comandos después de usar CREATE DATABASE como se mostró anteriormente para
crear la base de datos de la colección de animales. En estas instrucciones, "shell>"
representa el indicador de su intérprete de comandos.


Create the pet table:

  shell> mysql menagerie < cr_pet_tbl.sql

To load the pet table, use either of these commands:

  shell> mysql menagerie < load_pet_tbl.sql
  shell> mysqlimport --local menagerie pet.txt

To add Puffball's record, use this command:

  shell> mysql menagerie < ins_puff_rec.sql

Create the event table:

  shell> mysql menagerie < cr_event_tbl.sql

Load the event table:

  shell> mysqlimport --local menagerie event.txt
