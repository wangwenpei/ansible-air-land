「Deprecated」Ansible-Air-Land
========================================================================================

**This project was deprecated.**
**We suggest you use Kubernetes and [wangwenpei.docker](https://github.com/wangwenpei/ansible-docker) to maint your container environment. **

Deploy docker use docker-compose and manage by systemd.



Install
-------

```
ansible-galaxy install wangwenpei.airland
```

Config
----------
ansible.cfg

```
filter_plugins  = roles/wangwenpei.airland/plugins/filter
```


Role Variables
--------------

```
air_land_project: "project"
air_land_template_root: "<template-root>"
air_land_active_services:
  - services-name-1
  - services-name-2
docker_compose_interpreter: "/usr/bin/docker-compose"

```

Example Playbook
----------------

```
- name: Hello World
  hosts: all
  gather_facts: True
  environment:
        PATH: "/opt/local/bin:/usr/bin:/usr/local/bin:/usr/sbin:/usr/local/sbin"
  vars:
    ansible_python_interpreter: "/usr/bin/env python"
    air_land_project: "hello-world"
    air_land_template_root: "/tmp/templates/air-lands"
    air_land_active_services:
      - hello-world

  roles:
    - wangwenpei.air-land

  tags: "hello-world"
```


Known Bug
------------------

1. you have to set `air_land_template_root` if your ansible workflow stuck. 

    ```
    -e air_land_template_root=`pwd`/templates
    ```


License
-------

GPLv3

Author Information
------------------

Author: wangwenpei
