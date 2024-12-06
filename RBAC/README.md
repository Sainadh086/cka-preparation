
# Role Based Access Control (RABC)

RBAC provides required permissions to accesses the kubernetes components, so the workloads can be accesses securely.

Creating Roles
- Cluster Role:- The access is provided across the cluster and we can assign this role across the kubernetes cluster.
- Cluster Role Binding:- Bind will assign the role to the user or set of users.
- Role:- Role based accesse is restricted to the namespace.
- Role Binding:- It will bind the role as well as cluster role to the namespace.


```
# creating roles using command line

kubectl create clusterrole pod-reader-cli --verb=get,list,watch --resource=pod 

```


## Practicse questions with Solutions

All below questions are gathered from random websites only for practicse.


```
Task:-
Create a new ClusterRole named deployment-clusterrole, which only allows to create the following resource types:
✑ Deployment
✑ Stateful Set
✑ DaemonSet

Create a new ServiceAccount named cicd-token in the existing namespace app-team1.
Bind the new ClusterRole deployment-clusterrole to the new ServiceAccount cicd-token, limited to the namespace app-team1.

# using command line to create cluster role
kubectl create clusterrole deployment-clusterrole --verb=create --resource=deploy,sts,ds

# creating namespace as we don't have it
kubectl create ns app-team1


# creating service account
kubectl create service account cicd-token -n app-team1

# assign the role to service account
kubectl create rolebinding deployment-clusterrole-binding --clusterrole=deployment-clusterrole --serviceaccount=apps-team1:cicd-token

```




