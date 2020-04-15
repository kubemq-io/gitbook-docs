# Connect Your Cluster

## Inside Cluster \(Service-To-Service\)

### Connect within the same namespace

Each cluster deployment exposes 3 services with the prefix of your cluster name.

For example, kubemq-cluster as cluster name:

| Service | Name | Default Port |
| :--- | :--- | :--- |
| gRPC | kubemq-cluster-grpc | 50000 |
| Rest | kubemq-cluster-rest | 9090 |
| API | kubemq-cluster-api | 8080 |

### Connect from external namespace

Each cluster deployment exposes 3 services with the prefix of your cluster name.

Use [Kubernetes DNS resolving ](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/)for accessing cluster services.

For example, namespace is kubemq and cluster name is kubemq-cluster with cluster.local domain name:

| Service | Name | Default Port |
| :--- | :--- | :--- |
| gRPC | kubemq-cluster-grpc.kubemq.svc.cluster.local | 50000 |
| Rest | kubemq-cluster-rest.kubemq.svc.cluster.local | 9090 |
| API | kubemq-cluster-api.kubemq.svc.cluster.local | 8080 |

## Outside Cluster

### Connect with Node Port

Expose the required service via node port and access the service with host:port defined.

#### Configure gRPC Node Port

{% page-ref page="../configuration/configuration/set-grpc-interface.md" %}

#### Configure Rest Node Port

{% page-ref page="../configuration/configuration/set-rest-interface.md" %}

#### Configure Api Node Port

{% page-ref page="../configuration/configuration/set-api-interface.md" %}



### Connect with Kubemqctl as Proxy

Kubemqctl CLI tool provides a very useful command which port-forward all cluster services ports of selected cluster to localhost.

```text
kubemqctl set cluster proxy
```

