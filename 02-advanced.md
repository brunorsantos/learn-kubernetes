## Dns

Inside the same pod DNS is not needed, we can access direct by port using localhost:port.

DNS can be used to find pods running on the same cluster

One conteiner can access other DNS using:

```
Suposing and service called app1 trying to acess oher service called app2

It can access his own DNS using app1-service
It can access his own DNS using app2-service or app2-service.<namespace name> or  app2-service.<namespace name>.svc.local

```

![image](https://user-images.githubusercontent.com/20507162/126563752-ad918690-abb8-45c8-964d-551b40e3050d.png)


On kubernetes cluster there is a pod ruuning on the namespace kube-system using the service kube-dns. That all pods resolve the DNS using it.

![image](https://user-images.githubusercontent.com/20507162/126565758-9b96e797-7979-45a5-ab22-1371dfe63a51.png)

