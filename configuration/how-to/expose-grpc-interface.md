# Expose gRPC Interface

Expose gRPC port on NodePort

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --grpc-expose NodePort --grpc-node-port 30500
```
{% endtab %}

{% tab title="Helm" %}
```bash
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

#### More Configuration Options

{% page-ref title="gRPC Configuration" page="../cluster.md#grpc" %}


