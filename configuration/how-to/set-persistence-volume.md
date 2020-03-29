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
helm install kubemq-cluster --set volume.size=30Gi kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
```text

```
{% endtab %}
{% endtabs %}

