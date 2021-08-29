# Components

Kubernetes use different components.

## Pod

Is an abstraction over a container and typically meant to only run one in each
container. Each pod has its own IP address in the Kubernetes virtual network,
however, as containers are ephemeral these IP addresses are not permanent.

## Deployment

A deployment is a declarative way of creating pods.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: target-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: target-app
  template:
    metadata:
      labels:
        app: target-app
    spec:
      containers:
        - name: target
          image: target-server:test
          imagePullPolicy: IfNotPresent
```

## Service

A service allows exposing a set of pods to the virtual network. Each service has
a static IP address making it more reliable to refer than pod IPs. Services can
be both publicly exposed or only internal. They can also work as a load
balancers.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: target-service
spec:
  ports:
    - port: 80
      protocol: TCP
  selector:
    app: target-app
```

There are four types of services:

- **ClusterIP** Only reachable within cluster.
- **NodePort** Exposes service en each nodes on a static port.
- **LoadBalancer** Exposes service through load balancer. This is then handled
  by e.g. a cloud provider.
- **ExternalName** Allows using a `CNAME` record.

## Ingress

An ingress controller is responsible for routing external traffic into the
cluster.
