# Set Cluster Replicas

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |


## Exmaples

Set max delay seconds allowed to no more than one hour:

```bash
kubemqctl create cluster --queue-max-delay-seconds 3600
```

Change default of visibility to 3 minutes:

```bash
kubemqctl create cluster --queue-default-visibility-seconds 180
```
{% endtab %}

{% tab title="Helm" %}
## Values

| Value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |


## Exmaples

Set max delay seconds allowed to no more than one hour:

```bash
helm install kubemq-cluster  --set queue.maxDelaySeconds=3600 kubemq-charts/kubemq
```

Change default of visibility to 3 minutes:

```bash
helm install kubemq-cluster  --set queue.defaultVisibilitySeconds=180 kubemq-charts/kubemq
```
{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |


## Exmaples

Set max delay seconds allowed to no more than one hour:

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
  queue:
    maxDelaySeconds: 3600
```

Change default of visibility to 3 minutes:

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
  queue:
    defaultVisibilitySeconds: 180
```
{% endtab %}
{% endtabs %}

