# Set Cluster Name

Set implicit Kubemq cluster name

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --name your-kubemq-cluster-name
```
{% endtab %}

{% tab title="Helm" %}
```bash
helm install your-kubemq-cluster-name  kubemq-charts/kubemq
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
  name: your-kubemq-cluster-name
  namesapce: kubemq
spec:
  replicas: 3
```
{% endtab %}
{% endtabs %}

