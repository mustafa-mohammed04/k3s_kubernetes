## server
``` bash
mkdir -p /etc/rancher/k3s/
vim /etc/rancher/k3s/config.yaml
```
``` yaml
token: mustafa-token
node-ip: 192.168.16.52
```
``` bash
curl https://get.k3s.io | sh -s
sudo -i
kubectl get nodes 
kubectl get pods -A
```
## agent
``` bash
mkdir -p /etc/rancher/k3s/
vim /etc/rancher/k3s/config.yaml
```
``` yaml
server: https://192.168.16.52:6443
token: mustafa-token
node-ip: 192.168.16.53
```
``` bash
curl https://get.k3s.io | sh -s agent
```
