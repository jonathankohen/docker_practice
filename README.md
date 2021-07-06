# docker_practice

Working example of using Docker with Django!

## Running

`docker build -t <CUSTOM_NAME> -f Dockerfile .`

`docker run -it -p 8888:8888 <CUSTOM_NAME>`

## Optionally

`docker run -it -d -p 8888:8888 <CUSTOM_NAME>`

`docker ps` (find the ID of the container)

`docker stop <ID>`

`docker rm <ID>`
