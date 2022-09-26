# :computer: ROLE dginhoux.docker_stacks

## :scroll: DESCRIPTION

This ansible role deploy swarm stacks



## :nut_and_bolt: REQUIREMENTS

#### SUPPORTED PLATFORMS

This role require a supported platform. 
It will skip node with unsupported platform to avoid any compatibility problem.
This behaviour can be bypassed by settings this variable `asserts_bypass=True`.

| Platform | Versions |
|----------|----------|
| Debian | buster, bullseye |
| Fedora | 33, 34, 35, 36 |
| EL | 7, 8 |


#### ANSIBLE VERSION

Ansible >= 2.12


#### DEPENDENCIES

None.


## :inbox_tray: INSTALLATION

#### ANSIBLE GALAXY

```shell
ansible-galaxy install dginhoux.docker_stacks
```

#### GIT

```shell
git clone https://github.com/dginhoux/ansible_role.docker_stacks dginhoux.docker_stacks
```


## :rocket: USAGE

#### EXAMPLE PLAYBOOK

```yaml
- hosts: all
  roles:
    - name: start role dginhoux.docker_stacks
      ansible.builtin.include_role:
        name: dginhoux.docker_stacks
      vars:
        swarm_overlay_networks_list:
          - auth-public
          - ingress-public
          - log-public
          - mail-public
          - monitoring-public
          - mysql-public
          - postgres-public
          - redis-public
          - rp-public
          - supervision-public
          - socket-public
        swarm_stacks_action: deploy
        swarm_stacks_list:
          - compose: /mnt/gfs_lv_swarm_registry/registry-stack/registry-cache/docker-compose.yml
            name: registry-cache
            state: present
          - compose: /mnt/gfs_lv_swarm_registry/registry-stack/registry-build/docker-compose.yml
            name: registry-build
            state: present
        
```


## :factory: VARIABLES
#### DEFAULT VARIABLES
Role default variables from `defaults/main.yml` : 

| Variable Name | Value |
|---------------|-------|
|swarm_stacks_action | <pre> deploy </pre> |
|swarm_stacks_list | <pre> - compose: /mnt/gfs_lv_swarm_registry/registry-stack/registry-cache/docker-compose.yml<br>  name: registry-cache<br>  state: present<br>- compose: /mnt/gfs_lv_swarm_registry/registry-stack/registry-build/docker-compose.yml<br>  name: registry-build<br>  state: present<br> </pre> |
|swarm_overlay_networks_list | <pre> - auth-public<br>- ingress-public<br>- log-public<br>- mail-public<br>- monitoring-public<br>- mysql-public<br>- postgres-public<br>- redis-public<br>- rp-public<br>- supervision-public<br>- socket-public<br> </pre> |


#### CONTEXT VARIABLES

Those variables are located in `vars/*.yml` are used to handle OS differences ; One of theses is loaded dynamically during role
runtime using the `include_vars` module and set OS specifics variable's.





## :man: AUTHOR

[![Author](https://img.shields.io/badge/maintained%20by-dginhoux-e00000?style=flat-square)](https://github.com/dginhoux)


## :bookmark_tabs: LICENSE

[![License](https://img.shields.io/github/license/dginhoux/ansible_role.docker_stacks?style=flat-square)](https://github.com/dginhoux/ansible_role.docker_stacks/blob/master/LICENSE)