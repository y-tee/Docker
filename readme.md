### Running docker
https://fenics.readthedocs.io/projects/containers/en/latest/jupyter.html \
https://medium.com/the-code-review/top-10-docker-commands-you-cant-live-without-54fb6377f481 \
https://towardsdatascience.com/15-docker-commands-you-should-know-970ea5203421

#### Docker commands
get docker ip \
`sudo docker inspect <container-id> | grep '"IPAddress"' | head -n 1`

run new docker container \
`docker run -d -p 8888:8888 jupyter/pyspark-notebook`

check docker \
`docker ps -q`
`docker pa -a`: see all the past dockers that is also exitted

check docker logs and link \
`docker logs <container-id>`

docker copy to local \
`docker cp <docker-id>:/home/jovyan/<filename> "<path>"`

remove all docker container not running \
`docker rm $(docker ps -a -q)`


#### Spark Docker with jupyter: 
https://medium.com/@suci/running-pyspark-on-jupyter-notebook-with-docker-602b18ac4494 \
Need to replace localhost with docker ip by getting `docker-machine ip` on docker terminal \
overview of docker: https://www.dataquest.io/blog/docker-data-science/


#### ELK Docker: 
cd to docker yml file directory 

run docker compose \
`sudo docker-compose up`

check docker ip on local host \
`sudo docker-compose ps`

elk docker set-up : https://www.youtube.com/watch?v=PWUuyDrqvt0

#### Building flask docker image

[link](https://runnable.com/docker/python/dockerize-your-flask-application)

build docker image \
`sudo docker build -t {name}:latest .`

run docker \
`sudo docker run -d -p 5010:5010 {name}`

to mount a host directory to docker container, and not rebuild container anytime with code changes \
` docker run -d -p 5010:5010 --name credit-scoring --mount type=bind,source="$(pwd)",target=/app {name} apps.py` \
`docker run -d -p 5010:5010 --name {container name} -v "$(pwd)":/app {image name}:latest apps.py`

### Flask production with gunicorn and nginx
[gunicorn and nginx with docker compose](https://medium.com/technonerds/a-production-grade-machine-learning-api-using-flask-gunicorn-nginx-and-docker-part-2-c69629199037)

`docker-compose build` \
`docker-compose up`


[Dockerfile command difference](https://goinbigdata.com/docker-run-vs-cmd-vs-entrypoint/) \
*CMD enables change of arg at runtime*

Docker issues \
python have some [encoding issue](https://stackoverflow.com/questions/27931668/encoding-problems-when-running-an-app-in-docker-python-java-ruby-with-u) with docker need to add below in Dockerfile
```
RUN apt-get clean && apt-get -y update && apt-get install -y locales && locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
```
*update and install is not always needed unless locale error throw up*

If there's need to read other files in flask app.py, just name the path /app/filename (with condition of docker file dir named /app)

#### Docker Volume and mount
[Type of Persistant data in docker](https://stackoverflow.com/questions/47150829/what-is-the-difference-between-binding-mounts-and-volumes-while-handling-persist)

#### Dockerfile and Docker-compose
[Docker file builds docker image, while docker-compose specify config and orchestrate many docker containers](https://stackoverflow.com/questions/29480099/docker-compose-vs-dockerfile-which-is-better/45549372#45549372)

