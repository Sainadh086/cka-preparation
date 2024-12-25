# Networking

Kubernetes provides services where we can add it on top of the workload. If the pod gets replaced or deleted then the new pod will be getting assigned a new ip and it will be very hard to keep on updating the ips.  

Service provides various ways to expose our pod for communicating to other apps or end client. And it keeps on tracking the change of ip address.
We have 3 types in the service
    - ClusterIP: The service will get assigned with an IP from the cluster subnet.
    - NodePort: One of the port will be exposed on the cluster level to run the traffic from node to the pod.
    - Loadbalancer: Creates a loadbalancer for the service, where it also requires nodeport for diverting the traffic.

Network Policy restricts the network access to the pods, and the pods which are required to communicate can be allowed.