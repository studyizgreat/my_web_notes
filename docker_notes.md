## Docker notes 

- if you run docker command but it gives permission denied that is because the user you are using to run docker command does not have a group called, docker 
  -- sudo usermod -aG docker <username>
  -- sudo newgrp docker  

- Docker Commands: 
  -- docker ps  , to see the running containers
  -- docker ps -a , see all running and exited containers

### Docker Images and Containers 
- 
- 
- 
- 
- 

##### docker login 
- docker login
```
Docker Notes: docker login

USING WEB-BASED LOGIN

i Info → To sign in with credentials on the command line, use 'docker login -u <username>'


Your one-time device confirmation code is: VRKV-ZDPW
Press ENTER to open your browser or submit your device code here: https://login.docker.com/activate

Waiting for authentication in the browser…

WARNING! Your credentials are stored unencrypted in '/home/tamr/.docker/config.json'.
Configure a credential helper to remove this warning. See
https://docs.docker.com/go/credential-store/

Login Succeeded
``` 

- docker logout 
```
Docker Notes: docker logout
Removing login credentials for https://index.docker.io/v1/
```

- Docker pull and run mysql 
  -- The command i run is from the hub.docker.com
```
Docker Notes: docker run --name mysql-latest -v ~/datadir:/var/lib/mysql -e MYSQL_ROOT_PASSWORD
=Password0 -d mysql:latest
84e9e93a24ce5947d11b4b221b15e5404b69802f5283797be73040e9c2cb7214
Docker Notes: docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                                      NAMES
84e9e93a24ce   mysql:latest   "docker-entrypoint.s…"   6 seconds ago   Up 6 seconds   3306/tcp, 33060/tcp                                        mysql-latest
ff63be040aba   php:apache     "docker-php-entrypoi…"   5 hours ago     Up 4 hours     0.0.0.0:8000->80/tcp, [::]:8000->80/tcp                    php_server
e46d0004e7ce   mysql:latest   "docker-entrypoint.s…"   5 hours ago     Up 5 hours     33060/tcp, 0.0.0.0:33306->3306/tcp, [::]:33306->3306/tcp   mysql_server
```


