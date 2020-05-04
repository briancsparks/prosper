---
title: "Install Examples"
date: 2020-04-17T17:28:00-07:00
draft: false
weight: 3
---

## Raw (Apt) / Imstall Example

### From an Apt Repo

```sh
OS_CODENAME="$(lsb_release -cs)"

curl -L https://deb.nodesource.com/gpgkey/nodesource.gpg.key | sudo apt-key add -
echo "deb https://deb.nodesource.com/node_12.x ${OS_CODENAME} main" | sudo tee -a /etc/apt/sources.list.d/node.list
sudo apt-get update
sudo apt-get install -y --no-install-recommends nodejs
```

### From a PPA

```sh
sudo add-apt-repository -y ppa:jonathonf/vim
sudo apt-get update
sudo apt-get install -y --no-install-recommends vim
```

### From a PPA w/ Keyserver

```sh
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CC86BB64
sudo add-apt-repository -y ppa:rmescandon/yq
sudo apt update
sudo apt install -y --no-install-recommends yq
```

## Ansible Example

```yaml
- name: Install Packages
  apt:
    update_cache: true
    state: present
    name:
      - tree
      - git
  become: true
```

### From an Apt Repo

```yaml
- name: Add nodesource apt key
  apt_key:
    url: https://keyserver.ubuntu.com/pks/lookup?op=get&fingerprint=on&search=0x1655A0AB68576280
    id: "68576280"
    state: present
  become: true

- name: Add NodeSource repositories for Node.js.
  apt_repository:
    repo: "{{ item }}"
    state: present
  with_items:
    - "deb https://deb.nodesource.com/node_12.x {{ ansible_distribution_release }} main"
    - "deb-src https://deb.nodesource.com/node_12.x {{ ansible_distribution_release }} main"
  register: node_repo
  become: true

- name: Update apt cache if repo was added.
  apt: update_cache=yes
  when: node_repo.changed
  tags: ['skip_ansible_lint']
  become: true

- name: Ensure Node.js and npm are installed.
  apt:
    name: nodejs
    state: present
  become: true
```

### From a PPA

```yaml
- name: Add vim8
  apt_repository:
    repo: ppa:jonathonf/vim
    state: present
  become: true

- name: Install vim package
  apt:
    name: vim
    state: latest
    update_cache: yes
  become: true

```

## Cloud-Init Example

### From an Apt Repo

TBD

### From a PPA

TBD

### From a PPA w/ Keyserver

TBD

## Docker Example

### From an Apt Repo

TBD

### From a PPA

TBD

### From a PPA w/ Keyserver

TBD
