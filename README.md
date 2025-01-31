# express-mvc-framework
nodejs + express + mongodb to do MVC example

Youtube: [API Structure Your Nodejs REST API for beginner to Advanced](https://youtu.be/i4Pr81apfnU)

Blog: [backend nodejs](https://anonystick.com)

# How to use

### clone git

```
> git clone https://github.com/anonystick/structure-api-mvc-express-nodejs.git your-project
> cd your-project
> npm i
> npm run dev
```

# Try

[localhost](http://localhost:3132)


File:
```
install nginx 

1. Reverse Proxy Nginx
```bash
sudo apt-get install -y nginx 
run ip, not wokring then htto open secirity
cd /etc/nginx/sites-available

sudo vim default

location /api { 
 rewrite ^\/api\/(.*)$ /api/$1 break;
 proxy_pass  http://localhost:3000;
 proxy_set_header Host $host;
 proxy_set_header X-Real-IP $remote_addr;
 proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
}


sudo systemctl restart nginx
```

2. Add domain to nginx configuration


```bash
server_name shopdev.anonystick.com www.shopdev.anonystick.com;

location / {
    proxy_pass http://localhost:3000; 
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
}
```

3. add SSL to domain 

```bash
sudo add-apt-repository ppa:certbot/certbot
sudo apt-get update
sudo apt-get install python3-certbot-nginx
sudo certbot --nginx -d shopdev.anonystick.com
sudo certbot renew --dry-run
sudo systemctl status certbot.timer
```


location / {
    proxy_pass http://localhost:3000;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
}


sudo add-apt-repository ppa:certbot/certbot