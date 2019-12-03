# Custom nginxplus docker build

1. Build nginxplus docker image<br>
Place the Dockerfile in to the current directory, together with nginx-repo.crt and nginx-repo.key
```
docker build -t nginxplus .
```

2. Run it with your custom conf files<br>
Put your custom config files in /home/ec2-user/conf.d (for example)
```
docker run -d --name nginxplus1 -p 80:80 -v /home/ec2-user/conf.d:/etc/nginx/conf.d nginxplus
```
if you run SSL on nginxplus, just add one more "-p 443:443"<br>

3. Test
```
curl http://localhost
```

4. Modify the content of conf.d and reload nginx process
```
docker exec nginxplus1 nginx -s reload
```
Have fun!
