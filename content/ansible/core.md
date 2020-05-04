---
title: "Core"
date: 2020-05-01T23:19:03-07:00
draft: false
---

## OS

### mkdir -p

```sh
mkdir -p /var/jenkins_home
chown -R 1000:1000 /var/jenkins_home/
```

```yaml
- name: Recursively change ownership of a directory
  file:
    path:                 /var/jenkins_home
    state:                directory
    recurse:              yes
    owner:                1000
    group:                1000
```

### cp

```sh
cp files/kato/sshd-d-image-entrypoint.sh ~/kato-config/docker-context/sshd-d-image-entrypoint.sh
```

```yaml
- name:                   cp sshd-d-image-entrypoint.sh to instance
  copy:
    src:                  files/kato/sshd-d-image-entrypoint.sh
    dest:                 "{{ ansible_user_dir }}/kato-config/docker-context/sshd-d-image-entrypoint.sh"
    owner:                foo
    group:                foo
    mode:                 a+x
    mode:                 '0755'
    backup:               yes
```

```yaml
- name:                   cp sshd-d-image-entrypoint.sh to instance
  copy:
    src:                  files/kato/sshd-d-image-entrypoint.sh
    dest:                 "{{ ansible_user_dir }}/kato-config/docker-context/sshd-d-image-entrypoint.sh"
    owner:                foo
    group:                foo
    mode:                 a+x
    mode:                 '0755'
    backup:               yes
```

```yaml
- name:                   cp sshd-d-image-entrypoint.sh to instance
  copy:
    src:                  files/kato/sshd-d-image-entrypoint.sh
    dest:                 "{{ ansible_user_dir }}/kato-config/docker-context/sshd-d-image-entrypoint.sh"
    owner:                foo
    group:                foo
    mode:                 a+x
    mode:                 '0755'
    backup:               yes
```

### template

```sh
cp templates/kato/sshd-d-image.dockerfile ~/kato-config/docker-context/Dockerfile
```

```yaml
- name:                   sshd-d-image.dockerfile template
  template:
    src:                  kato/sshd-d-image.dockerfile
    dest:                 "{{ ansible_user_dir }}/kato-config/docker-context/Dockerfile"

```

## Docker

### docker build ...

```sh
docker build -t
```

```yaml
```

