---
title: "Install"
date: 2020-04-17T09:59:10-07:00
draft: false
weight: 2
---

## Raw (Apt) / Imstall

### From an Apt Repo

TBD

### From a PPA

TBD

### From a PPA w/ Keyserver

TBD

## Ansible

### From an Apt Repo

* `state: present` could be `state: latest`, but not recommended

```yaml
- name: Install Packages
  apt:
    update_cache: true
    state: present
    name:
      - foobar
      - bazbar
  become: true
```

### From a PPA

* `foostate` could be 'present'
  * `foostate` could be 'latest', but not recommended

```yaml
- name: Add vim8
  apt_repository:
    repo: ppa:foowho/foobar
    state: present
  become: true

- name: Install foobar package
  apt:
    name: foobar
    state: foostate
    update_cache: yes
  become: true
```

## Cloud-Init

### From an Apt Repo

TBD

### From a PPA

TBD

### From a PPA w/ Keyserver

TBD

## Docker

### From an Apt Repo

TBD

### From a PPA

TBD

### From a PPA w/ Keyserver

TBD

