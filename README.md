# ROLE dginhoux.docker_stacks



## DESCRIPTION

This ansible role deploy swarm stacks.



## REQUIREMENTS

#### SUPPORTED PLATFORMS

This role require a supported platform.<br />
It will skip node with unsupported platform to avoid any compatibility problem.<br />
This behaviour can be bypassed by settings the following variable `asserts_bypass=True`.

| Platform | Versions |
|----------|----------|
| Debian | buster, bullseye |
| Fedora | 33, 34, 35, 36 |
| EL | 7, 8 |

#### ANSIBLE VERSION

Ansible >= 2.12

#### DEPENDENCIES

None.



## INSTALLATION

#### ANSIBLE GALAXY

```shell
ansible-galaxy install dginhoux.docker_stacks
```
#### GIT

```shell
git clone https://github.com/dginhoux/ansible_role.docker_stacks dginhoux.docker_stacks
```


## USAGE

#### EXAMPLE PLAYBOOK

```yaml
- hosts: all
  roles:
    - name: start role dginhoux.docker_stacks
      ansible.builtin.include_role:
        name: dginhoux.docker_stacks
```


## VARIABLES

#### DEFAULT VARIABLES

Defaults variables defined in `defaults/main.yml` : 

```yaml
swarm_stacks_action: deploy
## rm value is used to force remove all stacks listed in the following list
# swarm_stacks_action: rm

swarm_stacks_list:
  - name: registry-cache
    state: present
    compose: /mnt/gfs_lv_swarm_registry/registry-stack/registry-cache/docker-compose.yml
  - name: registry-build
    state: present
    compose: /mnt/gfs_lv_swarm_registry/registry-stack/registry-build/docker-compose.yml

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
```

#### DEFAULT OS SPECIFIC VARIABLES

Those variables files are located in `vars/*.yml` are used to handle OS differences.<br />
One of theses is loaded dynamically during role runtime using the `include_vars` module and set OS specifics variable's.

`NOT USED BY THIS ROLE`


## AUTHOR

Dany GINHOUX - https://github.com/dginhoux



## LICENSE

MIT
