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



