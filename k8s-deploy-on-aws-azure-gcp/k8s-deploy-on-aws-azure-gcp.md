footer: Che-Chia David Chang, 2018
slidenumbers: true
![fit](docker.png)

# Docker tutorial

---

# Outline

- Run a docker container
- Use docker networks
- Use docker volumes
- Write a dockerfile and build a docker image
- Use docker registry and distribute your apps on Dockerhub

---

# What is [Docker](https://www.docker.com/)?

> "Docker - Build, Ship, and Run Any App, Anywhere"
-- docker official website

---

# What is [Docker](https://www.docker.com/)?

![inline](container-vm.png) ![inline](container-vm-2.png)

---

# [Docker Get Started](https://docs.docker.com/get-started/)

- [Install](https://docs.docker.com/install/)

```
$ docker version

Client:
 Version:      18.05.0-ce
 ...

$ docker ps

CONTAINER ID   IMAGE          COMMAND               CREATED             STATUS          
304f1e8af0b2   gcloud:latest  "gcloud auth login"   About an hour ago   Up About an hour... 

```

---

# Run a Docker container

- docker run

```
$ docker run hello-world

Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
ca4f61b1923c: Pull complete
Digest: sha256:ca0eeb6fb05351dfc8759c20733c91def84cb8007aa89a5bf606bc8b315b9fc7
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.
```

---

# Run a Docker container

- docker ps --all

```
CONTAINER ID IMAGE       COMMAND  CREATED        STATUS                     NAMES
482262308e60 hello-world "/hello" 11 seconds ago Exited (0) 10 seconds ago  epic_minsky
8a7534bee64b hello-world "/hello" 2 minutes ago  Exited (0) 2 minutes ago   angry_montalcini
```

- docker inspect 482262308e60 [NAME | ID]

```
    {
        "Id": "482262308e60b59135f4d39082b8c52ce1741c59e769fc332aca1a251aacd9c9",
       ...
        "HostConfig": {
          ...
           "NetworkMode": "default",
           ...
    }
```

---

# Use docker networks

```
$ docker run --help
Usage:	docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

$ docker run [--network=default] \
  --name my-nginx \
  --volume /some/content:/usr/share/nginx/html:ro \
  --publish 8080:80 \
  --detach \
  nginx
```

---

# Use docker networks

- Different network configurations

```
$ docker run --network default --publish 8080:80 ...
$ docker run --network host ...
```

---

# [Docker networks](https://docs.docker.com/network/)

- Bridge networks: communicate containers through bridge
- Host networks: use host’s port, ip...
- Container networks: (attach) to another container's network
- Overlay networks: communicate between multiple nodes
...

---

# Use docker volume

```
$ docker run [--network=default] --name my-nginx \
  --volume /some/content:/usr/share/nginx/html:ro \
  --publish 8080:80 \
  --detach \
  nginx
```
- volume[^1]:
  - /some/content: local directory path on host
  - /usr/share/nginx: volume path inside container

[^1]: Put nginx/html files in /some/content and let nginx serve it

---

# [Write a dockerfile](https://docs.docker.com/get-started/part2/)

- Prepare your app (example: app.py)
  - Prepare requirements.txt (app.py prerequsites)
- Write dockerfile
- Build image
- Docker run

```
$ vim Dockerfile
```

---

# [Write a dockerfile](https://docs.docker.com/get-started/part2/)

```
# Use an official Python runtime as a parent image
FROM python:2.7-slim

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
ADD . /app

# Install any needed packages specified in requirements.txt
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```

---

# [Write a dockerfile](https://docs.docker.com/get-started/part2/)

- Build image

```bash
$ ls
Dockerfile		app.py			requirements.txt

$ docker build -t friendlyhello .

$ docker image ls

REPOSITORY            TAG                 IMAGE ID
friendlyhello         latest              326387cea398
```

---

# [Write a dockerfile](https://docs.docker.com/get-started/part2/)

- Docker run
  - docker run
  - check `http://localhost:4000`
    - `http://0.0.0.0:80` inside container

```
$ docker run -p 4000:80 friendlyhello

$ docker ps
```

---

# Use docker registry

- [Docker hub](https://hub.docker.com/): Default
- [Docker hub nginx](https://hub.docker.com/_/nginx/)

```bash
$ docker pull nginx
```

---

# Use docker registry

- docker login
- docker tag
- docker push

```
$ docker login

$ docker tag friendlyhello [username/repository:tag]

$ docker tag friendlyhello chechiachang/friendlyhello:1
```

---

# Use docker registry

- docker push
- distribute
  - docker run [username/repository:tag]

```
$ docker push chechiachang/friendlyhello:1

# Run app on any other host
$ docker run chechiachang/friendlyhello:1
```

---
![fit](docker.png)

# Thank you

