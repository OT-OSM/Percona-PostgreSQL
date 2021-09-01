Osm Percona Postgres
====================

A high end ansible role to setup standalone or a cluster Percona Postgres with version support 11 and above with best practices in terms of security and performance tunning.

Version History
---------------

|**Date**| **Version**| **Description**| **Changed By** |
|----------|---------|---------------|-----------------|
|**Aug '31** | v0.0.1 | Initial Draft | [Abhishek Vishwakarma](abhishek.vishwakarma@opstree.com)|


Supported OS
------------
  * Ubuntu: bionic
  * Ubuntu: focal

Requirements
------------

There is no such requirements for the role.


Role Variables
--------------

The role variables are defined in the [vars](./defaults/main.yml). Here is the list of variables that is used in this role

|Variable | Description|
|---------|------------|
| version | Define version of postgresql|
| postgres_listen_addresses | Define Address when want to setup standalone|
|postgres_port |Define Address when want to setup standalone|
| users_creation | Set true when want to create user|
| database_creation| Set true when want to create database|
| replication | Set true for cluster configuration|
| replica_user| User of the postgreSQL|
| replica_pass | Group of the postgreSQL |

Inventory
----------
An inventory should look like this:-
```ini
[master]                 
192.168.1.198

[slave]
192.168.3.201

[postgres_cluster:children]
master
slave

[postgres_cluster:vars]
ansible_user=ubuntu
```

Example Playbook
----------------
Here is an example of playbook to execute this role:-

```yaml
---
- hosts: postgres_cluster
  roles:
    - role: percona_postgres
      become: yes
```
## Usage

There are multiple ways of executing the playbook according to your environment

- To run complete role

```shell
ansible-playbook -i hosts site.yml
```
- To create users

```shell
ansible-playbook -i hosts site.yml --tags "create_user"
```

- To create databases

```shell
ansible-playbook -i hosts site.yml --tags "create_database"
```

Future Proposed Changesense
-------
- Enable Failover in cluster configuration


Author Information
------------------
[Abhishek Vishwakarma](abhishek.vishwakarma@opstree.com)