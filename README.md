### 生成Docker镜像

```sh
docker build -t myblog /root/docker/django-uwsgi-nginx
```

### 启动docker容器

```sh
docker run -itd --link mysql:mysql -v /home/www/testproject:/home/docker/code/webproject --name webapp-project -p 8080:80 webproject bash
```
