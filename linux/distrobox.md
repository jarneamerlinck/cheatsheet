---
topic: distrobox
type: tool
site: https://github.com/89luca89/distrobox
status: core
included_topics:
  - cli
history:
  found: 2023/06/7
  tried: 2023/06/7
  used:  2023/06/7
  core: 2023/06/7
  hold: 
os:
  - linux
---
# Distrobox
[Readme](../README.md)

> Distrobox is compatibility tool to deploy other linux disto's as docker/podman containers

| What                             | Command                                                                       |
| -------------------------------- | :---------------------------------------------------------------------------- |
| Create box                       | ```distrobox-create --name box_name --image docker.io/library/ubuntu:22.04``` |
| Enter box                        | ```distrobox enter box_name```                                                |
| Stop box                         | ```distrobox stop box_name```                                                 |
| Set commit template              | ```git config commit.template ~/.gitmessage.txt```                            |
| Set excludesfile                 | ```git config --global core.excludesfile ~/.gitignore_global```               |
| Set git protocol for github auth | ```gh config set -h github.com git_protocol https```                          |
