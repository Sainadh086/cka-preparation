# Storage

By default pods have ephemeral storage, where the files are stored temporarily in pod. If a pod crashes it wont have any state.  
For some applications we need to store the state of the application for this we need to use permament storage options like storing in s3, EBS volumes ...etc.  
Kubernetes provides storage drivers which can create the persistent volumes (storage blocks) and can be attached to the pods.  

#### Persistent Volume

A PersistentVolume (PV) is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes. It is a resource in the cluster just like a node is a cluster resource.  

#### Storage Class

A StorageClass provides a way for administrators to describe the classes of storage they offer. Different classes might map to quality-of-service levels, or to backup policies, or to arbitrary policies determined by the cluster administrators. Kubernetes itself is unopinionated about what classes represent.  
We can connect various storage services available from cloud providers with the help of storage classes.

#### Persistent Volume Claims

A PersistentVolumeClaim (PVC) is a request for storage by a user. It is similar to a Pod. Pods consume node resources and PVCs consume PV resources. Pods can request specific levels of resources (CPU and Memory). Claims can request specific size and access modes (e.g., they can be mounted ReadWriteOnce, ReadOnlyMany, ReadWriteMany, or ReadWriteOncePod, see AccessModes).


#### Storage Policies

Reclaim Policy: When a PV is released (i.e., the PVC is deleted), Kubernetes uses a reclaim policy to decide what happens to the PV:
- Retain: The PV is not deleted and must be manually cleaned up.
- Delete: The PV is deleted along with the underlying storage resource.
- Recycle: The PV is scrubbed (data erased) and made available for re-use (this is deprecated in newer versions of Kubernetes).




#### Task

Task is to attach a PV to a pod running nginx, PV should use the local storage of the node at the path `/mnt/nginx-data/` to the pod path `/usr/share/nginx/html/` 