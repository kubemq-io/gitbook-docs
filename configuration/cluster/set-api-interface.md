# Set Api Interface

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --api-disabled | bool | false | Disable API interface |
| --api-port | int | 8080 | Set API port value |
| --api-expose | string | ClusterIP | Desired service type |
| --api-node-port | int |  | Desired port number in NodePort expose type |

Expose Options:

ClusterIP/NodePort/LoadBalancer

## Example

Expose Api interface port with a NodePort:

```bash
kubemqctl create cluster --api-expose NodePort --api-node-port 30700
```
{% endtab %}

{% tab title="Helm" %}
## Values

| value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| api.disabled | bool | false | Disable API interface |
| api.port | int | 8080 | Set API port value |
| api.expose | string | ClusterIP | Desired service type |
| api.nodePort | int |  | Desired port number in NodePort expose type |

Expose Options:

ClusterIP/NodePort/LoadBalancer

## Examples

Expose Api interface port with a NodePort:

```bash
helm install kubemq-cluster --set api.expose=NodePort,api-nodePort=30700  -n kubemq kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| disabled | bool | false | Disable API interface |
| port | int | 8080 | Set API port value |
| expose | string | ClusterIP | Desired service type |
| nodePort | int |  | Desired port number in NodePort expose type |

Expose Options:

ClusterIP/NodePort/LoadBalancer

## Example

Expose Api interface port with a NodePort:

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
  api:
    expose: NodePort
    nodePort: 30700
```
{% endtab %}
{% endtabs %}

