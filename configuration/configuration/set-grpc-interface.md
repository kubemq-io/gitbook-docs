# Set gRPC Interface

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --grpc-disabled | bool | false | Disable grpc interface |
| --grpc-port | int | 50000 | Set grpc port value |
| --grpc-expose | string | ClusterIP | Desired service type |
| --grpc-node-port | int |  | Desired port number in NodePort expose type |
| --grpc-buffer-size | int | 0 | Set subscribe message / requests buffer size to use on server |
| --grpc-body-limit | int | 0 | Set Max size of payload in bytes |

Expose Options:

ClusterIP/NodePort/LoadBalancer

## Example

Expose gRPC interface port with a NodePort:

```bash
kubemqctl create cluster --grpc-expose NodePort --grpc-node-port 30500
```
{% endtab %}

{% tab title="Helm" %}
## Values

| value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| grpc.disabled | bool | false | Disable grpc interface |
| grpc.port | int | 50000 | Set grpc port value |
| grpc.expose | string | ClusterIP | Desired service type |
| grpc.nodePort | int |  | Desired port number in NodePort expose type |
| grpc.bufferSize | int | 0 | Set subscribe message / requests buffer size to use on server |
| grpc.bodyLimit | int | 0 | Set Max size of payload in bytes |

Expose Options:

ClusterIP/NodePort/LoadBalancer

## Examples

Expose gRPC interface port with a NodePort:

```bash
helm install kubemq-cluster --set grpc.expose=NodePort,grpc-nodePort=30500  -n kubemq kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| disabled | bool | false | Disable grpc interface |
| port | int | 50000 | Set grpc port value |
| expose | string | ClusterIP | Desired service type |
| nodePort | int |  | Desired port number in NodePort expose type |
| bufferSize | int | 0 | Set subscribe message / requests buffer size to use on server |
| bodyLimit | int | 0 | Set Max size of payload in bytes |

Expose Options:

ClusterIP/NodePort/LoadBalancer

## Example

Expose gRPC interface port with a NodePort:

Run:

```bash
kubectl apply -f {below-yaml-file}
```

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

