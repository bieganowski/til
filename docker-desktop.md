Docker Desktop does not necessarily support creation of the default unix socket:
https://github.com/docker/for-mac/issues/7127

To temporarily fix this, one can check available sockets:
```shell
$ docker context ls
NAME              DESCRIPTION                               DOCKER ENDPOINT                                   KUBERNETES ENDPOINT                                                                     ORCHESTRATOR
default           Current DOCKER_HOST based configuration   unix:///var/run/docker.sock                       https://4592CC2DECBA67F08EBD08651C0D9446.yl4.eu-central-2.eks.amazonaws.com (default)   swarm
desktop-linux *   Docker Desktop                            unix:///home/<USERNAME>/.docker/desktop/docker.sock   
```

And export in the destination terminal
```shell
export DOCKER_HOST=unix:///home/<USERNAME>/.docker/desktop/docker.sock
```