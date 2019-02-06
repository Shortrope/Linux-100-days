# Nginx default config
Nginx main config file

    /etc/nginx/nginx.conf

Virtual hosts file in

    /etc/nginx/conf.d/

## nginx.conf

`events` block is required  
How connections are handled w the worker processes  

    events {
        worker_connections  1024;
    }

`http` block  
How http connections are handled  

`include`: include contents of file here


    http {
        include     /etc/nginx/mime.type
        include     /etc/nginx/conf.d/*.conf
    }

## default.conf
Nginx documentation  
http_server_core

### Barebones config file

    server {
        listen 80;
        root /usr/share/nginx/html;
    }

Test the configuration

    nginx -t