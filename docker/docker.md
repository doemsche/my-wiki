# Docker Commands

## Exit Container keeping it running
Ctrl-P / Ctrl-Q

## Volumes
A Volume is not dependent on a docker container lifecycle
```ruby
# remove container with volume:
docker container rm -vf containername

# Mount created volume from container to host using Volume API
# 0 check api
docker volume --help
# 1 create the volume
docker volume create --name html
# 2 mount
docker container run --name www -d -p 8080:80 -v html:/usr/share/nginx/html nginx

#Mount host folder into container
docker container run -v HOST_PATH:CONTAINER_PATH [OPTIONS] IMAGE [CMD]
# Case 1: the CONTAINER_PATH does not exist within the container
#bind local /tmp to container /data
docker container run -ti -v /tmp:/data alpine sh
# Case 2: the CONTAINER_PATH exists within the container
# mount local /tmp to /usr/share/nginx/html in container
```

## Maintenance (Clean all containers and images)

```ruby
#stop all containers
docker container stop $(docker container ls -aq)
#remove all containers
docker container rm $(docker container ls -aq)
#ungraceful remove all containers
docker container rm -f $(docker container ls -aq)

#remove all images
docker image rm $(docker image ls -q)

#list just die ids of contianers
docker container ls -aq

#inspect File dir on host
docker container inspect -f "{{ json .GraphDriver }}" c1 
```