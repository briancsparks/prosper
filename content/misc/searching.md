---
title: "Searching"
date: 2020-04-18T14:22:02-07:00
draft: false
---

## ag

### Highlight in a File (without Filtering)

```sh
cat playbook_util_instances.yaml | ag --passthrough shell
```

```sh
env | egrep -v '^(LS_COL|PATH)' | sort | ag --passthrough android
```

### Short, Summary

Just show the files that match, not the content, with count of matches in each file. (`--count`)

```sh
ag -c shell
```

```txt
playbook_util_instances.yaml:1
tasks/cdr0-deploy-user.yaml:1
tasks/docker-ansible-able.yaml:1
tasks/docker.yaml:1
tasks/cdr0-repos.yaml:1
playbook_webtier_instances.yaml:1
```

Just show the files that match.

```sh
ag -l shell
```

```txt
playbook_util_instances.yaml
tasks/cdr0-deploy-user.yaml
tasks/docker-ansible-able.yaml
tasks/docker.yaml
tasks/cdr0-repos.yaml
playbook_webtier_instances.yaml
```

Show files that do not match.

```sh
ag -L shell
```

```txt
playbook_controller_instances.yaml
ansible.cfg
inventory/ec2.ini
inventory/ec2.py
...
extensions/setup/role-update
extensions/setup/python_requirements.txt
vars/deploy-user.yaml
```

### Like 'fn'

The following is the same as `fn docker`.

```sh
ag -g docker
```

yields ->

```txt
tasks/docker-ansible-able.yaml
tasks/docker.yaml
handlers/docker.yaml
```

### Search Only in Files Whos Name Matches Pattern

```sh
ag -G webtier shell
```

yields ->

```txt
playbook_webtier_instances.yaml
55:      shell: |
```
