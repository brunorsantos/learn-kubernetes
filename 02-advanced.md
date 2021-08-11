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

## ConfigMap

Key values configrations to be used by containers in pods. (Not sensible data)

Containers can use it with files or ENV variables.

![image](https://user-images.githubusercontent.com/20507162/127057244-93f963a0-a9ba-4414-8949-f0ec50ceb306.png)

Using files we can create a volume inside the container to have it using a key with a whole configuration file for an application
Using ENV vars we can define a key one by one and use it on the spec of the pod


## Ingress Controller

Solucao que permite conexoes para o cluster. Permite facilmente exportar serviços que preciasm estar acessivis fora do cluster.
Basicamente é um loadbalancer

É possivel criar rules para direcionar para diferente serviços

É necessario que exista realmente uma pod executando que va servir como o ingress controller (pode se usar imagens especificas existentes para ingresses controllers)

Alem disso são criados os recursos do tipo `ingress` para direcionar para os services desejados de acordo com as rules



![image](https://user-images.githubusercontent.com/20507162/127062119-67d1f490-e7ac-4675-a200-6acbab239d25.png)


AS rules sao criadas via objetos do tipo ingress:

![image](https://user-images.githubusercontent.com/20507162/127903370-c2613f08-1ced-4327-aef7-298699ba4485.png)


O ingress controller pode ser definido normalmente com um deployment por exemplo com todos os recursos possiveis (readiness probe, liveness probe, etc)

## External DNS

![image](https://user-images.githubusercontent.com/20507162/127905321-a53907ad-0048-4cc1-9f73-53b41a6f9510.png)



## Pod Presets

Can inject information into pods ar runtime.

Secrets, voumes and Environments variables

We can use tags to identify pod we want to use the presets
