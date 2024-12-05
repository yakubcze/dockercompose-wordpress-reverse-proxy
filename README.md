
Launching
---------
**Build:**

    docker compose up -d

**Check if all containers are running:** 

	root@debian-hyperv:~/dockercompose-wordpress-reverse-proxy# docker ps
	CONTAINER ID   IMAGE              COMMAND                  CREATED         STATUS         PORTS                               NAMES
	dfae4fd85936   nginx:1.26.2       "/docker-entrypoint.…"   4 seconds ago   Up 2 seconds   0.0.0.0:80->80/tcp, :::80->80/tcp   proxy
	9d048125d281   wordpress:latest   "docker-entrypoint.s…"   4 seconds ago   Up 2 seconds   80/tcp                              wordpress2
	24a7b74149ae   wordpress:latest   "docker-entrypoint.s…"   4 seconds ago   Up 2 seconds   80/tcp                              wordpress1
	aef84ef134f3   wordpress:latest   "docker-entrypoint.s…"   4 seconds ago   Up 2 seconds   80/tcp                              wordpress3
	996cf3743d4d   mysql:5.7          "docker-entrypoint.s…"   4 seconds ago   Up 3 seconds   3306/tcp, 33060/tcp                 db

**Edit /etc/hosts**

	127.0.0.1  mly0037_1.eb212.local
	122.0.0.1  mly0037_2.eb212.local
	122.0.0.1  mly0037_3.eb212.local

**Test if reverse proxy is working correctly:**

wordpress1:

    root@Jakub-T480s:/home/jakub/dockercompose-nginx-reverse-proxy# curl mly0037_1.eb212.local
    	<!DOCTYPE html>
    	<html>
    	  <head>
    	    <title>STRANKA 1</title>
    	   </head>
    	   <body>
    	      <h1>mly0037_1.eb212.local</h1>
    	   </body>
    	</htm
wordpress2:
 
    root@Jakub-T480s:/home/jakub/dockercompose-nginx-reverse-proxy# curl mly0037_2.eb212.local
    <!DOCTYPE html>
    <html>
      <head>
        <title>STRANKA 2</title>
       </head>
       <body>
          <h1>mly0037_2.eb212.local</h1>
       </body>
    </html>

wordpress3:
