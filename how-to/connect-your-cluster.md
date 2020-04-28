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

### Connect with Load Balancer

#### Expose gRPC Load Balancer

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --grpc-expose LoadBalancer
```
{% endtab %}

{% tab title="Helm" %}
```text
helm install kubemq-cluster --set grpc.expose=LoadBalancer  -n kubemq kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqCluster
metadata:
  name: kubemq-cluster
  namesapce: kubemq
  labels:
    app: kubemq-cluster
spec:
  replicas: 3
  grpc:
    expose: LoadBalancer
```
{% endtab %}
{% endtabs %}

#### Expose Rest Load Balancer

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --rest-expose LoadBalancer
```
{% endtab %}

{% tab title="Helm" %}
```bash
helm install kubemq-cluster --set rest.expose=LoadBalancer  -n kubemq kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqCluster
metadata:
  name: kubemq-cluster
  namesapce: kubemq
  labels:
    app: kubemq-cluster
spec:
  replicas: 3
  rest:
    expose: LoadBalancer
```
{% endtab %}
{% endtabs %}

#### Expose Api Load Balancer

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --api-expose LoadBalancer
```
{% endtab %}

{% tab title="Helm" %}
```bash
helm install kubemq-cluster --set api.expose=LoadBalancer  -n kubemq kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqCluster
metadata:
  name: kubemq-cluster
  namesapce: kubemq
  labels:
    app: kubemq-cluster
spec:
  replicas: 3
  api:
    expose: LoadBalancer
```
{% endtab %}
{% endtabs %}

### Connect with Node Port

Expose the required service via node port and access the service with host:port defined.

#### Configure gRPC Node Port

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --grpc-expose NodePort --grpc-node-port 30500
```
{% endtab %}

{% tab title="Helm" %}
```text
helm install kubemq-cluster --set grpc.expose=NodePort,grpc-nodePort=30500  -n kubemq kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqCluster
metadata:
  name: kubemq-cluster
  namesapce: kubemq
  labels:
    app: kubemq-cluster
spec:
  replicas: 3
  grpc:
    expose: NodePort
    nodePort: 30500
```
{% endtab %}
{% endtabs %}

#### Configure Rest Node Port

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --rest-expose NodePort --rest-node-port 30600
```
{% endtab %}

{% tab title="Helm" %}
```text
helm install kubemq-cluster --set rest.expose=NodePort,rest-nodePort=30600  -n kubemq kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqCluster
metadata:
  name: kubemq-cluster
  namesapce: kubemq
  labels:
    app: kubemq-cluster
spec:
  replicas: 3
  rest:
    expose: NodePort
    nodePort: 30500
```
{% endtab %}
{% endtabs %}

#### Configure Api Node Port


{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --api-expose NodePort --api-node-port 30700
```
{% endtab %}

{% tab title="Helm" %}
```text
helm install kubemq-cluster --set api.expose=NodePort,api-nodePort=30700  -n kubemq kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqCluster
metadata:
  name: kubemq-cluster
  namesapce: kubemq
  labels:
    app: kubemq-cluster
spec:
  replicas: 3
  api:
    expose: NodePort
    nodePort: 30500
```
{% endtab %}
{% endtabs %}


### Connect with Kubemqctl as Proxy

Kubemqctl CLI tool provides a very useful command which port-forward all cluster services ports of selected cluster to localhost.

Run:

```bash
kubemqctl set cluster proxy
```

Will show :

```text
Current Kubernetes cluster context connection: kubernetes-local
? Select Kubemq cluster to Proxy kubemq/kubemq-cluster
Current Kubernetes cluster context connection: kubernetes-local
Connecting to kuberenets cluster...Ok.
start proxy for kubemq/kubemq-cluster-1. press CTRL C to close.
kubemq/kubemq-cluster-1:8080 -> 127.0.0.1:8080
kubemq/kubemq-cluster-1:9090 -> 127.0.0.1:9090
kubemq/kubemq-cluster-1:50000 -> 127.0.0.1:50000
```

