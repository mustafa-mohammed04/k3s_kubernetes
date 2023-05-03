# k3s_kubernetes
## Daemonsets
``` bash
vim ds.yaml
```

``` yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: nginx-ds
  namespace: default
spec:
  selector:
    matchLabels:
      name: nginx-ds
  template:
    metadata:
      labels:
        name: nginx-ds
    spec:
      tolerations:
      # these tolerations are to have the daemonset runnable on control plane nodes
      # remove them if your control plane nodes should not run pods
      - key: node-role.kubernetes.io/control-plane
        operator: Exists
        effect: NoSchedule
      - key: node-role.kubernetes.io/master
        operator: Exists
        effect: NoSchedule
      containers:
      - name: nginx-container
        image: nginx:alpine
```
``` bash
kuebctl apply -f ds.yaml
kubectl get ds
kubectl get pods 
```
## More info
 ``` bash
 kubectl get pods -o yaml
 kubectl get ds -o yaml
 ```
