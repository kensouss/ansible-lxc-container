# ansible lxc_container

## Description

This project help to create and configure lxc containers

Features:

* Create, and destroy containers
* install basic tools
* configure the ssh access
* configure the networking
* update /etc/hosts of the host machine
* update the list of created vms


## Requirements

The below requirements are needed on the host that executes the **lxc_container** module.
   
* lxc >= 1.0 # OS package
* python >= 2.6 # OS Package
* lxc-python2 >= 0.1 # PIP Package from https://github.com/lxc/python2-lxc

## container template options:

* distribution: centos
* release 7
* architecture amd64

## playbook

### Init a new or existing container

This playbook initiates a container and update the created_vms_list.

Example:

Initiate a new or existing container named **ansible-web-project**.

```bash
ansible-playbook -i architecture/hosts.ini architecture/container_manage.yml -t init --extra-vars "vm_name=ansible-web-project"
```

**Extra vars**

|   Extra var   |Mandatory         |   Default   |
|---------------|------------------|-------------|
|   vm_name     |:heavy_check_mark:|             |

### Install basic tools on a container

* openssh-server
* net-tools

Example:

Install basic tools on a container named **ansible-web-project**.

```bash
ansible-playbook -i architecture/hosts.ini architecture/container_manage.yml -t basics --extra-vars "vm_name=ansible-web-project"
```

**Extra vars**

|   Extra var   |Mandatory         |   Default   |
|---------------|------------------|-------------|
|   vm_name     |:heavy_check_mark:|             |

### Configure the container ssh access

Example:

Configure the container ssh access on a container named **ansible-web-project** for an user nammed **mohamed**.

```bash
ansible-playbook -i architecture/hosts.ini architecture/container_manage.yml -t ssh_config --extra-vars "vm_name=ansible-web-project vm_ssh_user=mohamed"
```
**Extra vars**

|   Extra var   |Mandatory         |   Default   |
|---------------|------------------|-------------|
|   vm_name     |:heavy_check_mark:|             |
|   vm_ssh_user |:x:               |    admin    |

### Configure the container networking

This playbook configure the container networking, add the /etc/hosts entry and update the created_vms_list.

Example:

Configure the container networking on a container named **ansible-web-project**, with container ip address equals to **10.0.3.22**.

```bash
ansible-playbook -i architecture/hosts.ini architecture/container_manage.yml -t network --extra-vars "vm_name=ansible-web-project vm_ip=10.0.3.22"
```

**Extra vars**

|   Extra var   |Mandatory         |   Default   |
|---------------|------------------|-------------|
|   vm_name     |:heavy_check_mark:|             |
|   vm_ip       |:heavy_check_mark:|             |

### Stop a container

Example:

Stop a container named **ansible-web-project**.

```bash
ansible-playbook -i architecture/hosts.ini architecture/container_manage.yml -t stop --extra-vars "vm_name=ansible-web-project"
```

**Extra vars**

|   Extra var   |Mandatory         |   Default   |
|---------------|------------------|-------------|
|   vm_name     |:heavy_check_mark:|             |

### Destroy a container

This playbook remove the container, remove the /etc/hosts entry and update the created_vms_list.

Example:

Destroy a container named **ansible-web-project**.

```bash
ansible-playbook -i architecture/hosts.ini architecture/container_destroy.yml --extra-vars "vm_name=ansible-web-project"
```

**Extra vars**

|   Extra var   |Mandatory         |   Default   |
|---------------|------------------|-------------|
|   vm_name     |:heavy_check_mark:|             |