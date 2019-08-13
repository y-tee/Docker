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

check docker logs and link \
`docker logs <container-id>`

docker copy to local \
`docker cp <docker-id>:/home/jovyan/<filename> "<path>"`


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

###### elk docker set-up : https://www.youtube.com/watch?v=PWUuyDrqvt0


