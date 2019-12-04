# Custom NGINX Plus docker image build
## Some of the advanced features that NGINX Plus can provide
* Load balancing + Session persistence based on cookies *
* Active health checks on status code and response body
* Service discovery using DNS
* Caching static content, API caching with cache‑purging
* HA: Keepalived + VRRP, state sharing for features including sticky‑Learn session persistence
* JWT authentication for APIs and OpenID Connect single sign‑on (SSO)
* NGINX WAF dynamic module
* Built‑in, real‑time graphical dashboard
* Integrate with ELK
* Streaming Media
* JavaScript Module for NGINX Plus
## Build nginxplus docker image
Place the Dockerfile in to the current directory, together with nginx-repo.crt and nginx-repo.key
```
docker build -t nginxplus .
```

## Run it with your custom conf files
Put your custom config files in /home/ec2-user/conf.d (example)
```
docker run -d --name nginxplus1 -p 80:80 -v /home/ec2-user/conf.d:/etc/nginx/conf.d nginxplus
```
if you run SSL on nginxplus, just add one more "-p 443:443"<br>

## Test
```
curl http://localhost
```

## Modify the content of conf.d and reload nginx process
Check the config syntax before reloading
```
docker exec nginxplus1 nginx -t
```
Reload nginx process
```
docker exec nginxplus1 nginx -s reload
```
Have fun!
