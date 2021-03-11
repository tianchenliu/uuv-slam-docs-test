# TensorFlow 2 

## Docker Run

```
docker pull tensorflow/tensorflow:latest-gpu-jupyter
```

```
docker run -it -p 1234:8888 -v ~/ws/docker_test_1/Docker:/tf/ latest-gpu-jupyter
# or
docker run --gpus all -it --rm tensorflow/tensorflow:latest-gpu
# or
docker run --gpus all -it --rm tensorflow/tensorflow:latest-gpu-jupyter
```

- `docker run`: start container from image
- `-it`: interactive mode
- `-p 1234:8888`: port mapping - port 1234 of local with 8888 of container
- `-v DIR`: mount directory
- `image_id (64d8717296f8)`: name of docker image where container is to be created

All images: `docker images`

Current running dockers: `docker ps`

Stop container: `docker stop`

Jupyter notebook: http://localhost:1234/

Remove a container: 

```
docker ps -a
docker rm [ID]

# For all exited containers
docker ps -a -f status=exited
docker rm $(docker ps -a -f status=exited -q)
```


