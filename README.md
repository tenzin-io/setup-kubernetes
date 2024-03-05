# README
This Ansible playbook role that helps setup a Kubernetes cluster.

## Inventory groups
- `bootstrap_node` - The initial node to setup a Kubernetes cluster.
- `control_plane` - The nodes that will join the cluster as controlplane nodes.
- `worker_nodes` - The nodes that will join the cluster to host regular workloads.

**Supported OSes**
- Debian 12 (bookworm)

### Component release pages
- <https://containerd.io/downloads/#releases>
- <https://github.com/opencontainers/runc/releases>
- <https://github.com/containernetworking/plugins/releases>
- <https://github.com/projectcalico/calico/releases>
- <https://github.com/aws/eks-distro/releases>
- <https://github.com/kubernetes-sigs/cri-tools/releases>
