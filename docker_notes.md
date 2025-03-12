### Docker notes 

- if you run docker command but it gives permission denied that is because the user you are using to run docker command does not have a group called, docker 
  -- sudo usermod -aG docker <username>
  -- sudo newgrp docker  

- Docker Commands: 
  -- docker ps  , to see the running containers
  -- docker ps -a , see all running and exited containers
  -- 
