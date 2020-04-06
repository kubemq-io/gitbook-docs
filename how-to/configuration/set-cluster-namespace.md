# Set Cluster Namespace

Set implicit Kubemq cluster namespace installation

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --namespace kubemq-namespace
```
{% endtab %}

{% tab title="Helm" %}
```bash
helm install kubemq-cluster  kubemq-charts/kubemq -n kubemq-namespace
```
{% endtab %}

{% tab title="kubectl" %}
Run:

```bash
kubectl apply -f {below-yaml-file}
```

```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqCluster
metadata:
  name: kubemq-cluster
  namesapce: kubemq-namespace
spec:
  replicas: 3
```
{% endtab %}
{% endtabs %}

