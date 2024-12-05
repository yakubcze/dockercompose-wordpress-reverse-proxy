
Launching
---------
**Create directories for wordpress instances:**
	
 	for i in {1..3}; do
  		mkdir wordpress$i
    	done

**Build:**

    docker compose up -d

**Check if all containers are running:** 

	root@debian-hyperv:~/dockercompose-wordpress-reverse-proxy# docker ps
	CONTAINER ID   IMAGE              		     COMMAND                  CREATED         STATUS         PORTS                               						    NAMES
	dfae4fd85936   jc21/nginx-proxy-manager:latest       "/init"                  4 seconds ago   Up 2 seconds   0.0.0.0:80-81->80-81/tcp, :::80-81->80-81/tcp, 0.0.0.0:443->443/tcp, :::443->443/tcp   proxy
	9d048125d281   wordpress:latest   		     "docker-entrypoint.s…"   4 seconds ago   Up 2 seconds   80/tcp                              						    wordpress2
	24a7b74149ae   wordpress:latest   		     "docker-entrypoint.s…"   4 seconds ago   Up 2 seconds   80/tcp                              						    wordpress1
	aef84ef134f3   wordpress:latest   		     "docker-entrypoint.s…"   4 seconds ago   Up 2 seconds   80/tcp                              						    wordpress3
	996cf3743d4d   mysql:5.7          		     "docker-entrypoint.s…"   4 seconds ago   Up 3 seconds   3306/tcp, 33060/tcp                 						    db

**Edit /etc/hosts**

	127.0.0.1  mly0037_1.eb212.local
	122.0.0.1  mly0037_2.eb212.local
	122.0.0.1  mly0037_3.eb212.local

**Configure the NGINX PROXY MANAGER**
	
 	127.0.0.1:81

  ![image](https://github.com/user-attachments/assets/a797c936-a779-4d44-9b8b-b87c94bee0e1)


**Test if reverse proxy is working correctly:**

wordpress1:

![image](https://github.com/user-attachments/assets/8077a19f-6291-4494-af6d-4d69106b1531)

wordpress2:
 
![image](https://github.com/user-attachments/assets/b1ba8888-01b8-4110-aa06-c946411bd4f3)


wordpress3:

...
