# Get Cluster Status

## Using Kubemqctl

```bash
kubemqctl get cluster
```

Will show:

```bash
Current Kubernetes cluster context connection: docker-desktop
NAME                   DESIRED  READY  IMAGE                           GRPC                           REST                            API                           LICENSE-TO  LICENSE-TYPE               LICENSE-EXPIRE
kubemq/kubemq-cluster  3        3      docker.io/kubemq/kubemq:latest  ClusterIP: 10.106.3.147:50000  ClusterIP: 10.109.245.198:9090  ClusterIP: 10.96.138.25:8080  John Doe   Community Max 3 Instances  2020-05-16 11:35:33
```

## Using kubectl

```bash
kubectl get kubemqclusters -n kubemq
```

Will show:

```bash
NAME             VERSION                          STATUS     REPLICAS   READY   GRPC                            REST                             API                            LICENSE-TYPE                LICENSE-TO   LICENSE-EXPIRE
kubemq-cluster   docker.io/kubemq/kubemq:latest   Deployed   3          3       ClusterIP: 10.106.3.147:50000   ClusterIP: 10.109.245.198:9090   ClusterIP: 10.96.138.25:8080   Community Max 3 Instances   John Doe    2020-05-16 11:35:33
```

