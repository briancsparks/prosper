---
title: "Tasks for Docker Commands"
date: 2020-05-02T16:53:24-07:00
draft: false
---

## docker build [...]

```sh
docker build -t jenkins-sshd-d .
```

```yaml
# docker build ...
- name:                                     docker build kato jenkins image
  docker_image:
    build:
      path:                                 "{{ ansible_user_dir }}/kato-config/docker-context"
    name:                                   jenkins-sshd-d
    source:                                 build
```

## docker run [...]

```sh
docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -d --name jenkins jenkins-sshd-d
```

```yaml
# docker run -p 8080:8080 -p 50000:50000 -p 2222:22 -v /var/jenkins_home:/var/jenkins_home -d --name jenkins jenkins-sshd-d
- name:                                     Docker run jenkins
  docker_container:
    name:                                   jenkins
    image:                                  jenkins-sshd-d
    detach:                                 true
    ports:
      - "8080:8080"
      - "50000:50000"
      - "2222:22"
    volumes:
      - /var/jenkins_home:/var/jenkins_home
```

