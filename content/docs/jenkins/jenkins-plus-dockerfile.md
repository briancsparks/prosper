---
title: "Jenkins + Dockerfile"
date: 2020-04-11T14:18:08-07:00
draft: false
---

### Jenkins in Docker

Give Jenkins access to the host docker socket, so any Docker commands that
Jenkins invokes are done on the host docker.

```Dockerfile
FROM jenkins
USER root

# TODO: im sure 1.13.1 is not the latest
RUN mkdir -p /tmp/download && \
    curl -L https://get.docker.com/builds/Linux/x86_64/docker-1.13.1.tgz | tar -xz -C tmp/download && \
    rm -rf /tmp/download/docker/dockerd && \
    mv /tmp/download/docker/docker* /usr/local/bin/ && \
    rm -rf /tmp/download && \
    groupadd -g 999 docker && \
    usermod -aG docker jenkins

USER jenkins
```

Then build it and run.

```sh
docker build -t jenkins-docker .
docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock --name jenkins -d jenkins-docker
```

* 8080 is the normal Jenkins HTTP port
* 50000 is the normal slave connection port
* `/var/jenkins_home` is the normal Jenkins data location
* `/var/run/docker.sock` is the docker socket
