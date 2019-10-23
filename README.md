# Zookeeper

Master
* [Installation and Dependencies](#installation-and-dependencies)
* [Tags](#tags)
* [Zookeeper Check](#zookeeper-check)
* [Examples](#examples)

This roles installs Apache Zookeeper server.

For more information about Zookeeper please visit
[zookeeper.apache.org/](http://zookeeper.apache.org/).


## Installation and Dependencies

To install dependencies, add this to your roles.yml

```YAML

---
- name: sansible.zookeeper
  version: v3.2.0
```

and run `ansible-galaxy install -p ./roles -r roles.yml`


## Tags

This role uses two tags: **build** and **configure**

* `build` - Installs Zookeeper server and all it's dependencies.
* `configure` - Configure and ensures that the Zookeeper service is running.


## Zookeeper Check

Purpose of the script is to confirm that all nodes have active conections
during start and/or deployment.  If node doesn't have any connections ZK
process is restarted. If node receives connections sript only returns stats.
Script can be also used to monitor nodes.


## Examples

```YAML
- name: Install Zookeeper Server
  hosts: sandbox

  pre_tasks:
    - name: Update apt
      become: yes
      apt:
        cache_valid_time: 1800
        update_cache: yes
      tags:
        - build

  roles:
    - name: sansible.zookeeper
```
