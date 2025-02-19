# ETCD

etcd is a strongly consistent, distributed key-value store that provides a reliable way to store data that needs to be accessed by a distributed system or cluster of machines. It gracefully handles leader elections during network partitions and can tolerate machine failure, even in the leader node.  

You can interact with etcd with etcdctl command line.

```
# here the basic commands to maintain high availability of our etcd during disasters

export ECTDCTL_API=3

# take the backup of etcd
etcdctl --endpoints=<etcd endpoint ip or url> --cacert=ca.cert --cert=user.crt --key=user.key \
snapshot save <snapshot name>

# once the snapshot is saved you can check the status
etcdctl --endpoints=<etcd endpoint ip or url> --cacert=ca.crt --cert=user.crt --key=user.key \
snapshot status <snapshot name>

# restore snapshot
etcdctl --endpoints=<etcd endpoint ip> --cacert=ca.crt --user=user.crt --key=user.key \
snapshot restore <snapshot-name> --data-dir <path for etcd folder> 

```

