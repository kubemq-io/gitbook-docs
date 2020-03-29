# Set Persistent Volume

Create Kubemq Cluster with 30Gi Persistent Volume Claim

{% tabs %}
{% tab title="Kubemqctl" %}
```text
kubemqctl create cluster -v 30Gi
```
{% endtab %}

{% tab title="Helm" %}
```text
helm install kubemq-cluster --set volume.size=30Gi -n kubemq kubemq-charts/kubemq 
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
  volume:
    size: 30Gi  
```
{% endtab %}
{% endtabs %}

