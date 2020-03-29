# Expose Rest Interface


Expose Rest interface port with a NodePort

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --rest-expose NodePort --rest-node-port 30600
```
{% endtab %}

{% tab title="Helm" %}
```bash
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
  nodePort: 30600
```
{% endtab %}
{% endtabs %}

#### [More Configuration Options](../cluster.md#rest)
