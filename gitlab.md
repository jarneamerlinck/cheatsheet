---
topic: gitlab
date: 2023/04/21
project: cheatsheet
type: note
---

# Gitlab
[ReadMe](README.md)

## Gitlab runner
```bash
docker run -d \
  --name gitlab-runner \
  --restart always \
  -v $PWD:$PWD \
  -v /var/run/docker.sock:/var/run/docker.sock \
  gitlab/gitlab-runner:latest
```