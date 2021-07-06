### Pods

Can have one more than one containeir that can easily communicate wit each other (just by using port)

### Kubelet

Stays in each node, is reposible to launch to pods. It connects on master node to manage it

### Kube-proxy

Stays in each node, where it change the list of pods lauched with their ip

### Service

Is public available(ususaly a load balancer). Has the list of nodes



![image](https://user-images.githubusercontent.com/20507162/124044019-c6700b00-d9e2-11eb-9096-bddc3d5edcc7.png)



### ReplicationController

A way to keep more than one pod running. It keeps the scale by controlling the number of replicas

### Deployments

Declarations that allows app to deploy and update. 
Manipulate da state of the application, without manual work. Creating new deployments, changing by version, rolling back.
Using replicas sets.
The pods are created and kept in the state by deployments

Get deployments:
```
kubectl get deployments --namespace=<namespace-name>
```

Get replica set(created by the deployment):
```
kubectl get rs --namespace=<namespace-name>
```
Get deployment status
```
kubectl rollout status deployment/<deployment name> --namespace=<namespace-name>
```

Get deployment history
```
kubectl rollout history deployment/<deployment name> --namespace=<namespace-name>
```
