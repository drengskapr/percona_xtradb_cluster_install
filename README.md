Percona xtradb cluster
=========

This role installs all packges required for running percona xtradb cluster with MySQL 5.7 along with percona monitoring and management client.

Requirements
------------

Ubuntu 18.04.+ x64 of Debian 10 x64

PXC setup
---------

After executing this role you need to setup pxc. This process consists of these steps:

1. Set password/ssl for mysql `root` user. 
2. Edit `wsrep.cnf` file on each node of your cluster. Add comma-separated ip-addresses/hostnames of all the cluster nodes to the end of line `wsrep_cluster_address=gcomm://`. Then add ip-address/hostname of current node to the end of line `wsrep_node_address=`. Set cluster and node name.
3. (Optional) Set up [SSL encryption](https://www.percona.com/doc/percona-xtradb-cluster/5.7/security/encrypt-traffic.html). This role copies ssl certificates from `files` folder. Generate them and put there before running the role. 
4. [Bootstrap the first node of your cluster](https://www.percona.com/doc/percona-xtradb-cluster/5.7/bootstrap.html#bootstrap).
5. [Add the rest of the nodes](https://www.percona.com/doc/percona-xtradb-cluster/5.7/add-node.html#add-node).
6. [Verify replication](https://www.percona.com/doc/percona-xtradb-cluster/5.7/verify.html#verify).

License
-------

BSD

