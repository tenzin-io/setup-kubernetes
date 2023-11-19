# README
This Ansible playbook role that helps setup a Kubernetes cluster.

## Inventory groups
- `bootstrap_node` - The initial node to setup Kubernetes
- `control_plane` - The nodes that will join the controlplane
- `worker_nodes` - The nodes that will host regular workloads

**Supported**
- Debian 12
- Nvidia GPUs

### Component release pages
- <https://containerd.io/downloads/#releases>
- <https://github.com/opencontainers/runc/releases>
- <https://github.com/containernetworking/plugins/releases>
- <https://github.com/projectcalico/calico/releases>
