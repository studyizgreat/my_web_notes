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

