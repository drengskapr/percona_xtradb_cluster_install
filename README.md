Percona xtradb cluster
=========

This role installs all packages required for running `percona xtradb cluster` with MySQL 8.0 along with `percona monitoring and management` client.

Requirements
------------

Ubuntu 18.04.+ x64 of Debian 10 x64

Example playbook
----------------

```
- name: Setting up PXC
  hosts: all
  remote_user: root
  roles:
    - pxc_install
  vars:
    mysql_root_password: <password>
```

PXC setup
---------

After executing this role you need to setup pxc. This process consists of these steps:
 
1. Edit `mysqld.cnf` file on each node of your cluster. Add comma-separated ip-addresses/hostnames of all the cluster nodes to the end of line `wsrep_cluster_address=gcomm://`. Then add ip-address/hostname of current node to the end of line `wsrep_node_address=`. Set cluster and node name.
2. (Optional) Set up [SSL encryption](https://www.percona.com/doc/percona-xtradb-cluster/8.0/security/encrypt-traffic.html). This role copies ssl certificates from `files` folder. Generate them and put there before running the role. 
3. [Bootstrap the first node of your cluster](https://www.percona.com/doc/percona-xtradb-cluster/8.0/bootstrap.html#bootstrap).
4. [Add the rest of the nodes](https://www.percona.com/doc/percona-xtradb-cluster/8.0/add-node.html#add-node).
5. [Verify replication](https://www.percona.com/doc/percona-xtradb-cluster/8.0/verify.html#verify).

License
-------

BSD

