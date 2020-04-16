# Set Rest Interface

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --rest-disabled | bool | false | Disable rest interface |
| --rest-port | int | 9090 | Set rest port value |
| --rest-expose | string | ClusterIP | Desired service type |
| --rest-node-port | int |  | Desired port number in NodePort expose type |
| --rest-buffer-size | int | 0 | Set subscribe message / requests buffer size to use on server |
| --rest-body-limit | int | 0 | Set Max size of payload in bytes |

Expose Options:

ClusterIP/NodePort/LoadBalancer

## Example

Expose Rest interface port with a NodePort:

```bash
kubemqctl create cluster --rest-expose NodePort --rest-node-port 30600
```
{% endtab %}

{% tab title="Helm" %}
## Values

| value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| rest.disabled | bool | false | Disable rest interface |
| rest.port | int | 9090 | Set rest port value |
| rest.expose | string | ClusterIP | Desired service type |
| rest.nodePort | int |  | Desired port number in NodePort expose type |
| rest.bufferSize | int | 0 | Set subscribe message / requests buffer size to use on server |
| rest.bodyLimit | int | 0 | Set Max size of payload in bytes |

Expose Options:

ClusterIP/NodePort/LoadBalancer

## Examples

Expose Rest interface port with a NodePort:

```bash
helm install kubemq-cluster --set rest.expose=NodePort,rest-nodePort=30600  -n kubemq kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| disabled | bool | false | Disable rest interface |
| port | int | 9090 | Set rest port value |
| expose | string | ClusterIP | Desired service type |
| nodePort | int |  | Desired port number in NodePort expose type |
| bufferSize | int | 0 | Set subscribe message / requests buffer size to use on server |
| bodyLimit | int | 0 | Set Max size of payload in bytes |

Expose Options:

ClusterIP/NodePort/LoadBalancer

## Example

Expose Rest interface port with a NodePort:

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
  rest:
    expose: NodePort
    nodePort: 30600
```
{% endtab %}
{% endtabs %}

