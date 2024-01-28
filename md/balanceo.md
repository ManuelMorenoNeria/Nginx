En este documento veremos como se crea un balanceador de carga con Nginx y Debian, para incrementar la disponibilidad de un servidor o aplicación que tenga mucha demanda.
 ## Paso 1
En la maquina que va hacer de balanceador instalamos nginx
![image](https://github.com/ManuelMorenoNeria/Nginx/assets/114908218/6b01e3b5-d0d4-4603-bc03-453648909bf6)


 ## Paso 2
Dentro del fichero /etc/nginx.nginx.conf añadimos dentro de hhtp {} las dos ips de nuestros servidores dentro de upstream
![image](https://github.com/ManuelMorenoNeria/Nginx/assets/114908218/84d1b404-d0e2-4dcd-8f60-7033a27aad90)

 ## Paso 3
Añadimos el proxy pass con el mismo server name que hemos puesto en el paso 2 en el fichero default de sites-availables de nginx

![image](https://github.com/ManuelMorenoNeria/Nginx/assets/114908218/49ebf733-7e18-4422-aeb3-c70ba8989e47)

 ## Paso 4
 Ya solo nos queda instalar nginx en nuestros dos servidores y modificar el index.html de cada uno de ellos para diferenciarlos.
 Ahora cada vez que accedamos a la ip de la maquina balanceadora, nos irá alternando entre los servidores que consulta, mostrandonos primero el index de server1, luego el de server2 y asi todas las veces que recarguemos la pagina.
 ![image](https://github.com/ManuelMorenoNeria/Nginx/assets/114908218/d919e918-80cd-4dde-a67b-60d2526d90bc)
![image](https://github.com/ManuelMorenoNeria/Nginx/assets/114908218/1b5311b8-eb40-4b6c-9bde-8c375d881c36)


¡Con esto ya tendriamos nuestro balanceador de cargas configurado!


Vamos a ver alguna configuración adicional:

Supongamosos que tenemos dos servidores pero el primero es 4 veces mas potente que el segundo. Esta característica de nuestros servidores podemos ajustarla en los ficheros de configuracion de nginx para que distribuya la carga de trabajo equitativamente.
se haría de la siguiente forma:
![image](https://github.com/ManuelMorenoNeria/Nginx/assets/114908218/c4b6d17c-e520-4c9c-9886-2f44b9defd25)

Ahora solo responderá el servidor dos cuando el servidor uno haya recibido 4 peticiones, es decir la quinta respuesta la dará el servidor 2.
Las 4 siguientes volvería a darlas el servidor 1, tal y como le hemos especificado




