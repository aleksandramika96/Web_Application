## Practical Web Development with: Docker, Django, Nginx, Redis and Gunicorn

[Go to Transylvanian Academy Web Site](https://www.transylvanianacademy.com/courses/1/)

### How to start MySQL Container
'''
docker run -d --name app-db --cpus 0.5 --memory 512m -e MYSQL_USER=alex -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=web_app_db --net app-net mysql:5.7
'''

### How to start WebApp Container
'''
docker run -itd --name web-app-1 -v "%cd%":/code --cpus 0.5 --memory 512m -p 8080:8000 --workdir /code --net app-net -e DOCKER_CONTAINER_ID=1 python:3.8
'''

### How to start the Load Tester
'''
docker run -itd --name load_tester --cpus 2 --memory 2g --net app-net node:latest
'''

### How to start the Load Balancer
'''
docker run -itd --name load_balancer --cpus 2 --memory 2g --net app-net -p 80:80 --workdir /etc/nginx/conf.d -v %cd%/static:/static nginx:1.15
*port 81:80 in my case
'''