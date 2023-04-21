---
topic: docker
type: tool
site: https://docker-curriculum.com/
status: core
included_topics:
  - infrastructure
  - CI/CD
  - cli
language:
  - bash
history:
  found: 2023/04/21
  tried: 2023/04/21
  used: 2023/04/21
  core: 2023/04/21
  hold:
os:
  - linux
  - windows
  - mac
---

# Docker
[Readme](../README.md)

## Private docker repository
- Run private docker [repo](https://github.com/dotcloud/docker-registry.git)
  - Alternative to [docker hub](https://hub.docker.com/)

## Installation
```bash
sudo apt update;sudo apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common;
curl -fsSL https://download.docker.com/linux/ubuntu/gpg \| sudo apt-key add -;
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable";
sudo apt update;sudo apt install docker-ce docker-ce-cli containerd.io;
sudo usermod -aG docker ${USER} && reboot
sudo setfacl --modify user:<user name or ID>:rw /var/run/docker.sock #migth be needed if you get an error about /var/run/docker.sock: connect: permission denied
```
## Commands
| What                              | Command                                                                                                                    |
| --------------------------------- | :------------------------------------------------------------------------------------------------------------------------- |
| pull image                        | ```docker pull imageName:tag```                                                                                            |
| remove image                      | ```docker rmi imageName:tag```                                                                                             |
| show running containers           | ```docker ps```                                                                                                            |
| show all containers               | ```docker ps -a```                                                                                                         |
| start container                   | ```docker start nameOfContainer```                                                                                         |
| stop container                    | ```docker stop nameOfContainer```                                                                                          |
| delete container                  | ```docker rm nameOfContainer```                                                                                            |
| attach container                  | ```docker attach nameOfContainer```                                                                                        |
| exit but keep running             | ```ctrl+q ctrl+p```                                                                                                        |
| inspect container                 | ```docker inspect nameOfContainer```                                                                                       |
| make image from running container | ```docker commit nameOfContainer```                                                                                        |
| show all images                   | ```docker images```                                                                                                        |
| tag image   (short) <br> (long)   | ```docker tag image_id imageName```  <br>     ```docker tag image_id website.com/imageName:version```                      |
| push image                        | ```docker push imageName```                                                                                                |
| create volume                     | ```docker volume create volName```                                                                                         |
| abs path for volume on host       | ```docker run image:tag -v /AbsPathOnHost:/AbsPathOnContainer```                                                           |
| run image                         | ```docker run -it --name nameOfContainer image:tag /bin/bash -p host_port:container_port -v volName:/AbsPathOnContainer``` |


## Dockerfile

see [dockerfile](https://docs.docker.com/engine/reference/builder/)