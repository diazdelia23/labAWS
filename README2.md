Para el Laboratorio 5 se buscaba tener la aplicación en Node js corriendo en contenedor de Docker y que pudiera comunicarse con la base de datos que se encontraba en otro contenedor de Docker. 

Lo que se hizo fue tener un archivo docker-compose.yml en el cual se pueden crear los contenedores y permite que se puedan comunicar entre ellos.

Luego en AWS se creó un cluster que tiene Load Balancer al que se puede subir la imagen de docker y que pueda comunicarse con la base de datos ya creada anteriormente en RDS.


1. Lo primero que hice fue instalar Docker y crear un Dockerfile con la imagen de node para poder correr la aplicación.
2. Se genera la imagen 
3. Se corre la imagen de manera local para comprobar que funciona
4. La imagen generada se sube a Docker hub
5. En AWS se utiliza ECS y se crea un container en el que se utiliza la imagen pública de docker hub
   deliamau/node-web-app:latest
6. Se realizan las configuraciones del cluster, su VPC, etc.
7. Se establece el load balancer
8. Se crea el cluster y se verifica que esté corriendo el task
9. Se utiliza el DNS público del Load Balancer para comprobar que la aplicación pueda ser accedida
10. Se realizó un docker-compose.yml en el cual se integra la imagen de mysql y poder generar la base de datos
11. Se genera un archivo init.sql en el cual se genera la base de datos, la tabla y algunos registros
12. Se modifica la app para que pueda conectarse a la base de datos
13. Se genera el archivo utilizando el comando "docker-compose up -p" 