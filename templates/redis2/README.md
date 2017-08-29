#Redis cluster on Rancher

Modify the rancher-compose.yml to include the scale necessary for the number of replicas you want (see below)
Deploy the stack using the included docker-compose.yml and rancher-compose.yml
Shell into any node and run the redis-trib command below corresponding to how many replicas you want.
0 Replicas:

Set scale in the rancher-copose.yml to 3
/usr/bin/redis-trib create --replicas 0 $( getent hosts redis-node-1.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-2.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-3.rancher.internal | awk '{ print $1 }'):6379
1 Replica:

This is the default config
Set scale in the rancher-compose.yml to 6
/usr/bin/redis-trib create --replicas 1 $( getent hosts redis-node-1.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-2.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-3.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-4.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-5.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-6.rancher.internal | awk '{ print $1 }'):6379
2 Replicas:

Set scale in the rancher-compose.yml to 9
/usr/bin/redis-trib create --replicas 2 $( getent hosts redis-node-1.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-2.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-3.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-4.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-5.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-6.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-7.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-8.rancher.internal | awk '{ print $1 }'):6379 $( getent hosts redis-node-9.rancher.internal | awk '{ print $1 }'):6379

