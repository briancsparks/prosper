---
title: "Ansible Plus Docker"
date: 2020-04-28T20:33:21-07:00
draft: false
---

From <https://docs.ansible.com/ansible/latest/modules/docker_image_info_module.html#docker-image-info-module>

Uses command (docker_image_info) to populate a result (result), then access the length of the result.

```yaml
- name: Inspect multiple images
  docker_image_info:
    name:
      - pacur/centos-7
      - sinatra
  register: result

- name: Make sure that both images pacur/centos-7 and sinatra exist locally
  assert:
    that:
      - result.images | length == 2
```
