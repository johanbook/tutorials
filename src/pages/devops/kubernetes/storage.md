# Storage

Pods are ephemeral and hence have no persistent storage. One must therefore
configure global volumes. It is important that the storage is available on all
nodes, not dependent on pod life-cycle and can survive a cluster crash.
