# README
This Ansible playbook helps initialize a Kubernetes cluster on a single-host.  Joining more nodes, requires only performing the `sysprep` role and applying the join command.

**Supported operating system**
- Debian 11

## Usage

### Initial Kubernetes node
- Setup the bootstrap node.  This bootstrap node is the first node in the Kubernetes cluster.

```
# Start the playbook and install Kubernetes
./main.yaml

# Setup the KUBECONFIG env variable and look around
export KUBECONFIG=/etc/kubernetes/admin.conf

kubectl get nodes
# NAME     STATUS   ROLES    AGE   VERSION
# kube-1   Ready    <none>   98s   v1.25.8

kubectl get pods -A
# NAMESPACE     NAME                                       READY   STATUS    RESTARTS   AGE
# kube-system   calico-kube-controllers-567c56ff98-rjnrs   1/1     Running   0          2m28s
# kube-system   calico-node-jwssl                          1/1     Running   0          2m28s
# kube-system   coredns-565d847f94-7nzht                   1/1     Running   0          2m44s
# kube-system   coredns-565d847f94-7w2l5                   1/1     Running   0          2m44s
# kube-system   etcd-kube-1                                1/1     Running   0          2m59s
# kube-system   kube-apiserver-kube-1                      1/1     Running   0          2m59s
# kube-system   kube-controller-manager-kube-1             1/1     Running   0          2m59s
# kube-system   kube-proxy-t642b                           1/1     Running   0          2m44s
# kube-system   kube-scheduler-kube-1                      1/1     Running   0          2m58s

# Print the worker node join command
kubeadm token create --print-join-command
```

### Adding worker nodes to the cluster
- Run the playbook with _only_ `sysprep`.
```
 ./main.yml -t sysprep

# Run the join command output from `kubeadm token create --print-join-command` on the bootstrap node
# kubeadm join ...

# Verify on a node that has a KUBECONFIG file for the cluster
kubectl get nodes
# NAME     STATUS   ROLES    AGE    VERSION
# kube-1   Ready    <none>   38m    v1.25.6
# kube-2   Ready    <none>   107s   v1.25.6
```
### Component release pages
- <https://containerd.io/downloads/#releases>
- <https://github.com/opencontainers/runc/releases>
- <https://github.com/containernetworking/plugins/releases>
- <https://github.com/projectcalico/calico/releases>
