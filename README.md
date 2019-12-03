# Custom nginx-plus docker image build

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
