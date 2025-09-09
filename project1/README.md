# SSH Connection Between Two Docker Container
<img width="1920" height="1080" alt="Screenshot 2025-09-02 141645" src="https://github.com/user-attachments/assets/7ba6a333-f8ba-4080-add5-7748d55f45bb" />

# how to do it 

- create the network
```yaml
docker network create my_docker_network
```

- Dockerfile for SSH Server: Create a Dockerfile to build an image with an SSH server.
- build the image
```yaml
docker build -t ssh_server_image .
```
- run the ssh server container
```yaml
 docker run -d --name ssh_server --network my_docker_network ssh_server_image
```
- Prepare the SSH Client Container:
```yaml
docker run -it --name ssh_client --network my_docker_network ubuntu:latest bash
```
- inside the client install:
```yaml
apt-get update && apt-get install -y openssh-client
ssh root@<SSH_SERVER_IP_ADDRESS>        # finally you can connet to the container
```

# concetps learned:
## Why is SSH not recommended to get shell access into docker?
Why not? Two reasons. First, unlike virtual machines, you should ideally run a single service per container because it makes it easier to debug problems in containers. And since you need to run OpenSSH in the container in order to use SSH, you're already at two services. Additionally, docker’s built-in method of using the `docker exec` command to run SSH commands makes it a lot easier than what was outlined above. With this command, you can access the shell or run remote commands without needing an SSH server. With that in mind, use SSH in a container only when you need a dockerized SSH service for a specific purpose.







