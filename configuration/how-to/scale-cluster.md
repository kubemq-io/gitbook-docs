# Scale Cluster

Scale Kubemq cluster replicas

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl kubemqctl scale cluster 5
```
{% endtab %}

{% tab title="Helm" %}
```bash
helm upgrade kubemq-cluster kubemq-charts/kubemq --set replicas=5
```
{% endtab %}
{% tab title="kubectl" %}
```bash
kubectl scale --replicas=5 kubemqclusters/kubemq-cluster
```
{% endtab %}
{% endtabs %}
