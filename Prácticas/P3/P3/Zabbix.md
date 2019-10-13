# Monitorización con Zabbix

David Gil Bautista

45925324M



Para la instalación de Zabbix he usado el siguiente [tutorial](https://www.unixmen.com/monitoring-server-install-zabbix-ubuntu-16-04/). He instalado el sistema de monitorización en una máquina corriendo en Ubuntu Server 16.04 con RAID1. He instalado Zabbix junto a MariaDB como gestor de MySQL y PHP 7.0 con Apache 2.



![](D:\Mega\Dropbox\UGR\4\ISE\Practicas\P3\1.PNG)

Tras instalar Zabbix en nuestro sistema podemos acceder desde el navegador de nuestro Host a la dirección IP de nuestra máquina y entrar a la configuración de Zabbix.

![](D:\Mega\Dropbox\UGR\4\ISE\Practicas\P3\2.PNG)

![](D:\Mega\Dropbox\UGR\4\ISE\Practicas\P3\3.PNG)

Al seleccionar la base de datos y poner el usuario y contraseña daba un error que se solucionó con darle más memoria a la caché de Zabbix.

![](D:\Mega\Dropbox\UGR\4\ISE\Practicas\P3\4.PNG)

Tras seguir todos los pasos y escoger el usuario y la base de datos que usará Zabbix para monitorizar el sistema habremos finalizado la instalación de Zabbix. Ahora podremos entrar con el usuario "Admin" y la contraseña "zabbix". Una vez dentro podemos observar que a pesar de que zabbix está corriendo en nuestro sistema, desde el navegador no lo reconoce.

![](D:\Mega\Dropbox\UGR\4\ISE\Practicas\P3\5.PNG)

![](D:\Mega\Dropbox\UGR\4\ISE\Practicas\P3\6.PNG)

Tras instalar todo aparecen los siguientes errores:



Connection to Zabbix server "localhost" refused. Possible reasons:

- 1. Incorrect server IP/DNS in the "zabbix.conf.php";

- 2. Security environment (for example, SELinux) is blocking the connection;

- 3. Zabbix server daemon not running;

- 4. Firewall is blocking TCP connection.

  Connection refused

Como podemos ver, el servidor está corriendo, por lo que podemos descartar la tercera razón.

![](D:\Mega\Dropbox\UGR\4\ISE\Practicas\P3\7.PNG)

Cambiamos la dirección IP del servidor a la de la máquina y tras reiniciar Zabbix sigue sin funcionar.

Comprobamos el estado de SELinux y lo desactivamos. Volvemos a reiniciar y sigue sin funcionar.

Abrimos los puertos 10051 y 10050 del firewall, mediante *sudo ufw allow 10051*, para evitar que deniegue la conexión. Comprobarmos que los puertos estén abiertos usando *netstat* y usamos traceroute para comprobar si se puede realizar la conexión y obtenemos una salida correcta, en teoría ya está arreglado. Reiniciamos el servidor de Zabbix y sigue sin funcionar :( 

