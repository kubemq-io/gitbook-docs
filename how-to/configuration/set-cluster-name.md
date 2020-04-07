# Set Cluster Name



{% tabs %}
{% tab title="Kubemqctl" %}
## Flags
| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --name | string | "kubemq-cluster"|set kubemq cluster name |


## Exmaple

Set implicit Kubemq cluster name:

```bash
kubemqctl create cluster --name your-kubemq-cluster-name
```
{% endtab %}

{% tab title="Helm" %}

## Values
No values defined for cluster name.

## Exmaple
Set implicit Kubemq cluster name:

```bash
helm install your-kubemq-cluster-name  kubemq-charts/kubemq
```
{% endtab %}

{% tab title="kubectl" %}

## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| name | string | "kubemq-cluster"|set kubemq cluster name |


## Exmaple
Set implicit Kubemq cluster name:
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

