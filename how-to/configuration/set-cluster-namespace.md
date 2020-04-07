# Set Cluster Namespace



{% tabs %}
{% tab title="Kubemqctl" %}

## Flags
| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --namespace | string | "kubemq"|set kubemq cluster namespace |

## Exmaple
Set implicit Kubemq cluster namespace installation:

```bash
kubemqctl create cluster --namespace kubemq-namespace
```
{% endtab %}


{% tab title="Helm" %}

## Values
No values defined for cluster namespace.

```bash
helm install kubemq-cluster  kubemq-charts/kubemq -n kubemq-namespace
```
{% endtab %}

{% tab title="kubectl" %}

## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| namespace | string | "kubemq-cluster"|set kubemq cluster name |
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

