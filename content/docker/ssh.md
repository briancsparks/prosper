---
title: "SSH"
date: 2020-04-11T14:15:08-07:00
draft: false
weight: 2
---

## Add sshd to Any Image

For example, add sshd to Jenkins.

```dockerfile
FROM {{ docker_image_for_sshd | default('jenkins/jenkins:latest') }}

USER root

# install git, curl, openssh server, and remove host keys
RUN apt-get update                                    && \
    apt-get install -y --no-install-recommends           \
        openssh-server                                && \
    mkdir /var/run/sshd                               && \
    rm -rf /var/lib/apt/lists/*                       && \
    rm -rf /etc/ssh/ssh_host_*

#USER ${user}

# expose ssh port
EXPOSE 22

# Make sure host keys are regenerated before sshd starts
COPY entrypoint.sh /entrypoint.hs

#ENTRYPOINT ["/entrypoint.sh"]
ENTRYPOINT ["/sbin/tini", "--", "/entrypoint.sh"]
```

With this as the entrypoint.sh script, to regenerate the container's ssh keys.

```sh
#!/bin/bash
dpkg-reconfigure openssh-server
service ssh start

# NOTE: use this if sshd is the only long-running process:
#/usr/sbin/sshd -D

# May have to start some other process
#/usr/local/bin/jenkins.sh
```
