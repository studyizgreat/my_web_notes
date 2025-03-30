
### Podman container 
- sudo dnf install podman # to install podman 
- sudo dnf install -y podman-docker # to install command masking with docker 
- 
```
$ sudo dnf list podman*
Updating Subscription Management repositories.
Last metadata expiration check: 1:27:17 ago on Sun 30 Mar 2025 03:35:28 PM CEST.
Installed Packages
podman.x86_64                                    4:5.2.2-15.el9_5                          @rhel-9-for-x86_64-appstream-rpms
podman-docker.noarch                             4:5.2.2-15.el9_5                          @rhel-9-for-x86_64-appstream-rpms
Available Packages
podman-catatonit.x86_64                          2:4.2.0-11.el9_1                          rhel-9-for-x86_64-appstream-rpms
podman-gvproxy.x86_64                            2:4.6.1-9.el9_3                           rhel-9-for-x86_64-appstream-rpms
podman-plugins.x86_64                            4:5.2.2-15.el9_5                          rhel-9-for-x86_64-appstream-rpms
podman-remote.x86_64                             4:5.2.2-15.el9_5                          rhel-9-for-x86_64-appstream-rpms
podman-tests.x86_64                              4:5.2.2-15.el9_5                          rhel-9-for-x86_64-appstream-rpms
```

- Podman was developed using go language 
``` 
$ podman version
Client:       Podman Engine
Version:      5.2.2
API Version:  5.2.2
Go Version:   go1.23.6 (Red Hat 1.23.6-2.el9_5)
Built:        Mon Mar 17 14:03:54 2025
OS/Arch:      linux/amd64
```
- To test the container 
- podman container run hello-world 

- image list 
```
$ podman image list
REPOSITORY              TAG               IMAGE ID      CREATED        SIZE
localhost/podman-pause  5.2.2-1742216634  33f7c9943b4a  2 hours ago    813 kB
quay.io/podman/hello    latest            5dd467fce50b  10 months ago  787 kB
docker.io/library/php   8.0-apache        3357132d6ece  16 months ago  465 MB
```

- List running containers 
```
$ podman container list
CONTAINER ID  IMAGE       COMMAND     CREATED     STATUS      PORTS       NAMES
```

- List stopped containers 
``` 
$ podman container list --all
CONTAINER ID  IMAGE                        COMMAND               CREATED             STATUS                         PORTS       NAMES
39df0b767274  quay.io/podman/hello:latest  /usr/local/bin/po...  About an hour ago   Exited (0) About an hour ago               infallible_gauss
3652fc834159  quay.io/podman/hello:latest  /usr/local/bin/po...  About a minute ago  Exited (0) About a minute ago              charming_yonath
```

- To show the whole output of the container run 
- podman container start -a <container_name> # if the container has exited it will show the whole output

- removing the container 
- podman container rm <container-id> 

- listing images 
```
$ podman image list
REPOSITORY              TAG               IMAGE ID      CREATED        SIZE
localhost/podman-pause  5.2.2-1742216634  33f7c9943b4a  2 hours ago    813 kB
quay.io/podman/hello    latest            5dd467fce50b  10 months ago  787 kB
docker.io/library/php   8.0-apache        3357132d6ece  16 months ago  465 MB
```

- finding images on multiple registries # I have truncated the output   
```
$ podman image search postgres
NAME                                                                    DESCRIPTION
registry.access.redhat.com/openshift3/postgresql-apb                    Ansible Playbook Bundle application definiti...
registry.access.redhat.com/openshift3/postgresql-92-rhel7               PostgreSQL 9.2 database server
registry.access.redhat.com/rhscl/postgresql-95-rhel7                    PostgreSQL server 9.5 for OpenShift and gene...
.
.
docker.io/fredboat/postgres                                             PostgreSQL 10.0 used in FredBoat's docker-co...
docker.io/trainlineeurope/postgres                                      Extended version of official Postgres https:...
docker.io/debezium/postgres                                             PostgreSQL for use with Debezium change data...
docker.io/blacklabelops/postgres                                        Postgres Image for Atlassian Applications
```

- finding image on a specific repo 
```
$ podman image search docker.io/nginx
NAME                                              DESCRIPTION
docker.io/library/nginx                           Official build of Nginx.
docker.io/nginx/nginx-ingress                     NGINX and  NGINX Plus Ingress Controllers fo...
docker.io/nginx/nginx-prometheus-exporter         NGINX Prometheus Exporter for NGINX and NGIN...
docker.io/antrea/nginx                            Nginx server used for Antrea e2e testing
```

- another example with quay 
```
$ podman image search quay.io/nginx
NAME                                                            DESCRIPTION
quay.io/kubernetes-ingress-controller/nginx-ingress-controller  NGINX Ingress controller built around the [K...
quay.io/redhattraining/hello-world-nginx
quay.io/ukhomeofficedigital/nginx-proxy                         # OpenResty Docker Container  [![Build Statu...
quay.io/dtan4/nginx-basic-auth-proxy
quay.io/cloud-bulldozer/nginx
```

- to have a specific registry for your case edit /etc/container/registries.conf 
- search for unqualified-search-registries 
```
unqualified-search-registries = ["registry.access.redhat.com", "registry.redhat.io", "docker.io"]
```

- pulling the image 
```
$ podman image pull docker.io/httpd
Trying to pull docker.io/library/httpd:latest...
Getting image source signatures
Copying blob c61868f0ad74 done   |
Copying blob 6e909acdb790 done   |
Copying blob 4f4fb700ef54 done   |
Copying blob 9f9b03a66afb done   |
Copying blob 084c58879b9a done   |
Copying blob 09bf08b13dbd done   |
Copying config 83d9381983 done   |
Writing manifest to image destination
83d938198316505b3aebd52bed1e54e5f2a49591cc41e09a30f480e5c00ea0cf
```

- Seeing the layers of the image 
```
$ podman image tree httpd:latest
Image ID: 83d938198316
Tags:     [docker.io/library/httpd:latest]
Size:     152.2MB
Image Layers
├── ID: 1287fbecdfcc Size: 77.84MB
├── ID: 9d413e5ee67a Size:  2.56kB
├── ID: 76215ba5e655 Size: 1.024kB
├── ID: 01e7031c14a5 Size:  11.4MB
├── ID: 186933b2ccd8 Size: 62.96MB
└── ID: e59fe47decd1 Size: 3.584kB Top Layer of: [docker.io/library/httpd:latest]
```

- Inspecting the image 
```
$ podman image inspect hello-world  # truncated 
[
     {
          "Id": "5dd467fce50b56951185da365b5feee75409968cbab5767b9b59e325fb2ecbc0",
          "Digest": "sha256:43de9874507eaa8ffd88eac885b672b1dfc57cc583d9ad920850f97f19809f8f",
          "RepoTags": [
               "quay.io/podman/hello:latest"
          ],
                    "created_by": "/bin/sh -c #(nop) COPY file:dcd0ec8c82666e48d3c5cfa9555c2b9c61a535c7697ac25beb65cc991d33833c in /usr/local/bin/podman_hello_world ",
                    "empty_layer": true
               },
               {
               "quay.io/podman/hello:latest"
          ]
     }
]
```

- To find what program will run use 
```
$ podman image inspect hello-world|grep CMD
                    "created_by": "/bin/sh -c #(nop) CMD [\"/usr/local/bin/podman_hello_world\"]"
```

- all Four commands work 
```
$ podman container list
CONTAINER ID  IMAGE       COMMAND     CREATED     STATUS      PORTS       NAMES
$ podman ps
CONTAINER ID  IMAGE       COMMAND     CREATED     STATUS      PORTS       NAMES
$ podman ps -a
CONTAINER ID  IMAGE       COMMAND     CREATED     STATUS      PORTS       NAMES
$ podman container list --all
CONTAINER ID  IMAGE       COMMAND     CREATED     STATUS      PORTS       NAMES
```

- if you run like this it will run in the foreground
```
$ podman container run httpd
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 192.168.0.19. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 192.168.0.19. Set the 'ServerName' directive globally to suppress this message
[Sun Mar 30 15:37:12.570845 2025] [mpm_event:notice] [pid 1:tid 1] AH00489: Apache/2.4.63 (Unix) configured -- resuming normal operations
[Sun Mar 30 15:37:12.570969 2025] [core:notice] [pid 1:tid 1] AH00094: Command line: 'httpd -D FOREGROUND'
^C[Sun Mar 30 15:37:15.111862 2025] [mpm_event:notice] [pid 1:tid 1] AH00491: caught SIGTERM, shutting down
```

- if you want to run with the interactive shell you can use the -it option as well as the command that will run as /bin/bash 
- you can understand the different below. 

- podman container stop <container_id> command works

- this is same as docker ps -a 
```
$ podman container list -all
CONTAINER ID  IMAGE                           COMMAND     CREATED             STATUS                       PORTS       NAMES
108319f09252  docker.io/library/httpd:latest  /bin/bash   About a minute ago  Exited (137) 22 seconds ago  80/tcp      distracted_merkle
```
- now below container i will run in foreground and stop that 
```
$ podman container run httpd
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 192.168.0.19. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 192.168.0.19. Set the 'ServerName' directive globally to suppress this message
[Sun Mar 30 15:43:27.505102 2025] [mpm_event:notice] [pid 1:tid 1] AH00489: Apache/2.4.63 (Unix) configured -- resuming normal operations
[Sun Mar 30 15:43:27.505211 2025] [core:notice] [pid 1:tid 1] AH00094: Command line: 'httpd -D FOREGROUND'
^C[Sun Mar 30 15:43:30.975061 2025] [mpm_event:notice] [pid 1:tid 1] AH00491: caught SIGTERM, shutting down
```
- you can see from below output the command without interactive was httpd-foreground
```
$ podman container list --all
CONTAINER ID  IMAGE                           COMMAND           CREATED        STATUS                      PORTS       NAMES
923a97ba8dcf  docker.io/library/httpd:latest  httpd-foreground  8 minutes ago  Exited (0) 8 minutes ago    80/tcp      romantic_ritchie
108319f09252  docker.io/library/httpd:latest  /bin/bash         7 minutes ago  Exited (137) 6 minutes ago  80/tcp      distracted_merkle
71888d54636f  docker.io/library/httpd:latest  httpd-foreground  2 minutes ago  Exited (0) 2 minutes ago    80/tcp      keen_knuth
```
- $ podman container run --name www -it httpd /bin/bash

- To remove all the stopped containers you can use  
- podman container prune 
```
$ docker container prune
Emulate Docker CLI using podman. Create /etc/containers/nodocker to quiet msg.
WARNING! This will remove all non running containers.
Are you sure you want to continue? [y/N] y
923a97ba8dcfcba5dc83cd529690cd2724e510c8e804d04a44ad30f90a0bfdd5
108319f09252b82cfdd4920a034d0dafe3e0a45916013ecf146f03acbcd01b48
71888d54636f42829cb06b683a3b7b50ddcb86349dbffe0269ee8e9e1a8d251b
47b0e7a862c3bb1ed1b260fda77501eed421d14074c1e9898877ea5f895f165b
```
- list is now empty 
``` 
$ podman container list --all
CONTAINER ID  IMAGE       COMMAND     CREATED     STATUS      PORTS       NAMES
```

- These work the same as docker 
- -p 80:80 
- -d background 

### Volumes 
- podman container run --name=www -d -it -p 8080:80 -v /home/user/dir:/usr/local/apache2/htdocs httpd
- some topics to relook 
	- /etc/subuid 
	- /etc/subgid
	- selinux in container 

### Container as a service 
- systemd startup a container 
- setsebool -P container_manage_cgroup on 
- podman generate systemd --new --name www > /etc/systemd/system/www.service
- systemctl daemon-reload 
- systemctl enable --now www
- systemctl start www  < this will create a new container so make sure the previous was removed. 
- podman container list < make sure it does not exist  

### Create your Dockerfile 
- First line of every Dockerfile is FROM 
FROM node 
- ENV is for environment variables 
ENV MONGO_DB_USERNAME=admin \
MONGO_DB_PWD=password

- RUN is used to run any type of linux command 
- RUN mkdir -p /home/app 

- COPY command executes on the host and copies files from host to the container 
- COPY . /home/app  
- it is copying file from the current host directory to the container /home/app 

- WORKDIR is like cd into a directory 
- WORKDIR /app 

- COPY instruction 
- COPY hello.txt /absolute/path/in/container
- COPY hello.txt relative/path/to/workdir 

- .dockerignore file can also make the files ignore just like .gitignore

- CMD ["node","server.js"] 
- Note you can have multiple RUN commands but CMD is the entry point only one command 

- Dockerfile is a fix name 
- docker build -t my-app:1.0 . 

- docker logs  <container> 

- Conclusion: 
- FROM , specifies the base image 
- FROM ubuntu:20.04

- RUN , Executes commands in a new layer on top of the current image 
- RUN apt-get update && apt-get install -y python3

- CMD , provides command to run within the container 
- CMD ["python3", "app.py"]

- WORKDIR, set the working directory for any subsequent instruction 
- WORKDIR /app 

- COPY . /app 

- ADD , similar to COPY but also supports extracting tar files and fetching files from URLs 
- ADD https://example.com/file.tar.gz /app/ 

- EXPOSE , Informs Docker that the container listens on the specified network ports at runtime 
- EXPOSE 80 

- ENV sets environment variables 
- ENV APP_ENV=production 

- ENTRYPOINT, configures container that will run as an executable 
- ENTRYPOINT ["python3", "app.py"]

- VOLUME , creates a mount point with the specified path and marks it as a holding externally mounted 
- VOLUME ["/data"]

- USER , Sets the username or UID to use when running the image and for any RUN , CMD , and ENTRYPOINT instruction that follow it. 
- USER appuser 

- LABEL version="1.0"

- ARG VERSION=1.0 
- ONBUILD , Add a trigger instruction to the image that will be executed when the image is used as a base for another bulid 
- ONBUILD RUN apt-get update && apt-get install -y vim 

- STOPSIGNAL , sets the system call signal that will be sent to the container to exit 
- STOPSIGNAL SIGTERM 

- HEALTHCHECK: Tells Docker how to test a container to check that it is still working.
- HEALTHCHECK CMD curl --fail http://localhost:8080/ || exit 1

- SHELL: Allows the default shell used for the shell form of commands to be overridden.
- SHELL ["/bin/bash", "-c"]


