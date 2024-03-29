# ROLE dginhoux.docker_stacks



## DESCRIPTION

This ansible role deploy swarm stacks.



## REQUIREMENTS

#### SUPPORTED PLATFORMS

| Platform | Versions |
|----------|----------|
| Debian | all |
| EL | all |
| Fedora | all |
| Ubuntu | all |

#### ANSIBLE VERSION

Ansible >= 2.13

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
  tasks:
    - name: start role dginhoux.docker_stacks
      ansible.builtin.include_role:
        name: dginhoux.docker_stacks
```


## VARIABLES

#### DEFAULT VARIABLES

Defaults variables defined in `defaults/main.yml`

#### EXAMPLES VARIABLES

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
  - name: test1
    state: present
    force: false
    scope: swarm
    driver: overlay
    enable_ipv6: false
    attachable: false
    internal: false
    # labels: 
    # ipam_config: 
    # ipam_driver: 
    # ipam_driver_options: 
    driver_options:
      com.docker.network.bridge.name: test1

  - name: test2
    state: present
    force: false
    scope: swarm
    driver: overlay
    enable_ipv6: false
    attachable: false
    internal: false
    # labels: 
    # ipam_config: 
    # ipam_driver: 
    # ipam_driver_options:
    driver_options:
      com.docker.network.bridge.name: test2
```

#### DEFAULT OS SPECIFIC VARIABLES

Those variables files are located in `vars/*.yml` are used to handle OS differences.<br />
One of theses is loaded dynamically during role runtime using the `include_vars` module and set OS specifics variable's.

`NOT USED BY THIS ROLE`


## AUTHOR

Dany GINHOUX - https://github.com/dginhoux



## LICENSE

MIT
