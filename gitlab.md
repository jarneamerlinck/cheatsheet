# Gitlab
[ReadMe](README.md)

## gitlab runner
```bash
docker run -d \
  --name gitlab-runner \
  --restart always \
  -v $PWD:$PWD \
  -v /var/run/docker.sock:/var/run/docker.sock \
  gitlab/gitlab-runner:latest
```