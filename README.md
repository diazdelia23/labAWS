# labAWS
labAWS

1. lo primero que realicé fue la base de datos (RDS) en MySQL a la cual me conecté desde MySQL Workbench y desde ahí creé mi tabla y agregué algunos datos para pruebas, modifiqué también el security group para que no me asignara una IP diferente cada vez que me quería conectar

2. Luego creé mi aplicación CRUD en Node.js con la que podía obtener información, agregar, editar y eliminar información de la base de datos a la que me conecté y luego subí mi código a un repositorio de github

3. Creé una instancia de EC2 en AWS a la cual le instalé node.js y git para poder clonar mi repositorio y ejecutar mi app desde la instancia, para ello también tuve que habilitar le puerto 3000 desde el cual ejecutaba mi aplicación.

4. Para poder crear mi Autoscaling Group, creé una imagen de la instancia en donde ejecuto mi app.

5. Luego, creo mi Launch Configuration en el que agrego los comandos con los que va a iniciar la instancia y la app al encenderse cuando se agreguen más instancias a través del autoscaling. Con ello va a poder repartirse a través del Load Balancer. Los comandos son los siguientes:

#!/bin/bash
cd /home/ec2-user/labAWS/src
/home/ec2-user/.nvm/versions/node/v10.16.0/bin/node app.js

6. Ya con la imagen, puedo crear mi Autoscaling Group en el cual determino las reglas que deseo para que puedan aumentar o reducirse mis instancias las cuales quiero que sean con la imagen de a primera instancia que creé.

7. Después creé el Load Balancer, establezco los puertos y demás configuración.

8. En mi Autoscaling asigno qué Load Balancer voy a utilizar, el cuál es el que creé anteriormente. Ahí ya puedo ver las instancias que mi autoscaling va a crear y confirmar si están en servicio o no.

9. Para probar mi Load Balancer lo realicé mendiante el DNS el cual me direccionaba a alguna de mis IP de las instancias creadas y en servicio.

10. Luego, para la prueba de carga, realicé stress en una de mis instancias a manera que se activaran las políticas de mi autoscaling y me generó 2 máquinas virtuales. Al finalizar la prueba y bajar el rendimiento de mi instancia, fueron terminadas debido a la política que había configurado.
