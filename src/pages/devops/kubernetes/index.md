# Kubernetes

Kubernetes, sometimes shortened to K8s, is an open-source cluster manager
developed by Google. It offers

- **Availability** No down time
- **Scalability** High performance
- **Disaster recovery** Backup

There is a master which manages several nodes, each typically running in its own
machine. The master exposes a key-value store (etcd) to its child nodes.

## Types of Nodes

As mentioned earlier, there are two types of nodes; workers and masters.

### Worker node

Each worker node needs the following to be installed:

- Container runtime
- Kubelet, interface between container and node.
- Kube Proxy, intelligently routes requests (e.g. pods on same node are
  preferred over other nodes)

### Master process

Each master process has four services running:

- **API Server**, the interface. Also handles authentication.
- **Scheduler**. Responsible for starting and stopping pods. It connects to the
  Kubelet in a node with itself then communicates with the container runtime.
- **Controller manager** Detect cluster state changes. If a pod dies it asks
  scheduler to schedule a new pod.
- **etcd** Is a key-value store that keep tracks of the state of the cluster.

One typically runs multiple masters where API server is load balanced and etcd
use a distributed storage.

This is sometimes referred to as the control plane.

### Namespaces

Namespaces are an efficient way of organizing components. This stops e.g. name
clashes to cause component overriding. Resources can also be limited on a
namespace level.

## See also

- [Components](./components.md)
- [Storage](./storage.md)
