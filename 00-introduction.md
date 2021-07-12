



## list contexts
```
kubectl config get-contexts
```

## Change context
```
kubectl config use-context <name>
```

## Pod useful commands

```
kubectl get pod //Get information about all running pods
```

```
kubectl describe pod <pod> //Describe one pod
```

```
kubectl expose pod <pod> --port=444 --name=frontend //Expose the port of a pod (creates a new service)
```

```
kubectl port-forward  <pod> 8080:3000 //Port forward the exposed por port to your local machine
```

```
kubectl exec  <pod> --command //Execute a command on the pod
```

```
kubectl describe pod <pod name>  --namespace=<namespace-name> 
```


