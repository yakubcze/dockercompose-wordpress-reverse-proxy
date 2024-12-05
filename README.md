
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
	CONTAINER ID   IMAGE                             COMMAND                  CREATED          STATUS          PORTS                                                                                  NAMES
	24f38ee94051   jc21/nginx-proxy-manager:latest   "/init"                  50 seconds ago   Up 28 seconds   0.0.0.0:80-81->80-81/tcp, :::80-81->80-81/tcp, 0.0.0.0:443->443/tcp, :::443->443/tcp   nginx-proxy-manager
	8b371cc62f30   wordpress:latest                  "docker-entrypoint.s…"   50 seconds ago   Up 28 seconds   80/tcp                                                                                 wordpress2
	3585bb4314d8   wordpress:latest                  "docker-entrypoint.s…"   50 seconds ago   Up 28 seconds   80/tcp                                                                                 wordpress3
	bed3a97dc78e   wordpress:latest                  "docker-entrypoint.s…"   50 seconds ago   Up 28 seconds   80/tcp                                                                                 wordpress1
	5fe9d7853164   mysql:5.7                         "docker-entrypoint.s…"   50 seconds ago   Up 29 seconds   3306/tcp, 33060/tcp                                                                    db


**Edit /etc/hosts**

	127.0.0.1  mly0037_1.eb212.local
	122.0.0.1  mly0037_2.eb212.local
	122.0.0.1  mly0037_3.eb212.local

**Setup reverse proxy in the web interface**

	http://127.0.0.1:81
	(admin@example.com/changeme)
	
**Test if reverse proxy is working correctly:**

wordpress1:

![image](https://github.com/user-attachments/assets/8077a19f-6291-4494-af6d-4d69106b1531)

wordpress2:
 
![image](https://github.com/user-attachments/assets/b1ba8888-01b8-4110-aa06-c946411bd4f3)


wordpress3:

...
