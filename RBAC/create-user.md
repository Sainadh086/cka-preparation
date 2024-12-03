# Creating Users

In kubernetes we use cert based authentication for authorizing users.

### Steps for creating certs

First create certs for users and authenticate it with kubernetes.

```
- openssl genrsa -out user.key 2048
- openssl req -new -key user.key -out user.csr -subj "/CN=<username>"
```

#### Sign the certificate with Kubernetes CA

```
openssl x509 -req -in user.csr -CA /etc/kubernetes/certs/ca.crt \
    -CAkey /etc/kubernetes/certs/ca.key  \
    -CAcreateserial -out user.crt -days 365
```

Create kubeconfig with the above created certs for connecting kubectl to the cluster.

```
kubectl config set-credentials <username> \
  --client-certificate=user.crt \
  --client-key=user.key

kubectl config set-context <context-name> \
  --cluster=kubernetes \
  --user=<username>

kubectl config use-context <context-name>
```



