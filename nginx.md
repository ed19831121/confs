nginx 	-s 	<signal>
		quit 	— graceful 	shutdown
		stop 	— fast 		shutdown
		reload 	— reloading the configuration file
		reopen 	— reopening the log files
---
server		port
location 	uri		<-	from
root		directory	<-	to

server {
    location / {
        root /data/www;
    }

    location /images/ {
        root /data;
    }
}
---
One of the frequent uses of nginx is setting it up as a proxy server, which means a server that 
	receives 	requests, 
	passes 		them 		to 	the proxied servers, 
	retrieves 	responses 	from 	them, and 
	sends 		them 		to 	the clients. 

被代理服务器：
server {
    listen 8080;
    root /data/up1;

    location / {
    }
}

代理服务器：
server {
    location / {
        proxy_pass http://localhost:8080;
    }

    location /images/ {
        root /data;
    }
}

---

server {
    location / {
        fastcgi_pass  localhost:9000;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_param QUERY_STRING    $query_string;
    }

    location ~ \.(gif|jpg|png)$ {
        root /data/images;
    }
}

In PHP,	the SCRIPT_FILENAME parameter is used for determining the script name, 
and 	the QUERY_STRING    parameter is used to  pass request parameters. 

The resulting configuration would be: 
