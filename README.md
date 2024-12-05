Original:
---------
[Docker compose : Nginx reverse proxy with multiple containers](http://www.bogotobogo.com/DevOps/Docker/Docker-Compose-Nginx-Reverse-Proxy-Multiple-Containers.php)

Consolidated to a single docker-compose.yml file

Launching
---------
**Build:**

    docker compose up -d

**Check if all containers are running:** 

    root@Jakub-T480s:/home/jakub/dockercompose-nginx-reverse-proxy# docker ps
    CONTAINER ID   IMAGE        COMMAND                  CREATED         STATUS         PORTS                               NAMES
    d9384cafd95b   nginx:1.12   "nginx -g 'daemon of…"   8 minutes ago   Up 8 minutes   0.0.0.0:80->80/tcp, :::80->80/tcp   proxy
    f475ce1e8750   nginx:1.12   "nginx -g 'daemon of…"   8 minutes ago   Up 8 minutes   80/tcp                              site2
    024e38bfd73d   nginx:1.12   "nginx -g 'daemon of…"   8 minutes ago   Up 8 minutes   80/tcp                              site1

**Edit /etc/hosts**


	127.0.0.1  mly0037_1.eb212.local
	122.0.0.1  mly0037_2.eb212.local

**Test if reverse proxy is working correctly:**

site1:

    root@Jakub-T480s:/home/jakub/dockercompose-nginx-reverse-proxy# curl mly0037_1.eb212.local
    	<!DOCTYPE html>
    	<html>
    	  <head>
    	    <title>STRANKA 1</title>
    	   </head>
    	   <body>
    	      <h1>mly0037_1.eb212.local</h1>
    	   </body>
    	</html>
 site2:
 
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

