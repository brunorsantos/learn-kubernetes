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

### Services

Logical bridge between the "mortal" pods and other services or end-users.
kubeclt expose command create a service.
When creating a service you choose a pod by the label and inform the port of this pod you want to wrap ( by name of the port defined on the pod)
When creating a service you need to define a port to be exposed with a type. The NodePort type can be acessed externaly 


 Describe one service
 ```
 kubeclt describe svc <hello>
 ```
 Show all service
 ```
 kubeclt get svc <hello>
 ```
 
 ### Label
 
 Key/values attached to objects 
 
 labels can be used to services redirect requests to pods. Or label can be used to make pods only be in certain pods.
 
 ### Healthchecks (Liveness Probe)
 
 We can put into a deployment. Adding a livenessProbe into the spec. In the configuration we put a initial delay and a delay for each healthcheck. 
 Tip: Using edit deployment we can see the specification of it:
 
 ```
 kubectl edit deployment deployment/<deployment-name> --namespace=<namespace-name>
 ```
 
 ### ReadinessProbe
 
 Indicates if the container is ready to serve. It does not restart the container like que livenesse probe, just removes the ip address from the service.
 In geneal both liveness probe and readiness probe are configured.
 The readinesse probe guarantees the the pod will be READY to serve requests after the health in the pod with the delay configured in the properties pass.
 
 ### Pod State
 
Pods has a status field, that `kubectl get pods` shows 
  
Running status means that the bound has been bound to a node, all containers in the pod are created  and at least one container is running or starting/restarting

Pending: Pods has been accepeted but is not running. Image can be still downloading, resouce limits...
Succeeded: All containers are terminated and will not be restarted
Failed: All containers are terminated and one of them returned a failure code

PodConditions:

- PodScheduled
- Ready
- Initialized
- Unschedulable
- ContainersReady


### Pod Lifecycle


![image](https://user-images.githubusercontent.com/20507162/125522986-00414580-e085-467f-86a8-d17e65d41515.png)




![image](https://user-images.githubusercontent.com/20507162/125522591-0236c038-a1f1-47ca-bc95-dc5d4616e883.png)



