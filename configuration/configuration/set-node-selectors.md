# Set Node Selectors


{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --node-selectors-keys| string map | "" |set node selectors key-value (map)|

## Example

Set node selectors

```bash
kubemqctl create cluster --node-selectors-keys key1=value1,key2=value2
```
{% endtab %}


{% tab title="Helm" %}
## Values

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| nodeSelectors.keys| string map | "" |set node selectors key-value (map)|

## Example

Set node selectors

```bash
helm install kubemq-cluster  --set nodeSelectors.keys "key1=value1,key2=value2"  kubemq-charts/kubemq
```
{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| keys| string map | "" |set node selectors key-value (map)|

## Example

Set node selectors

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
  nodeSelectors:
    keys:
      key: value
      key2: value2
```
{% endtab %}
{% endtabs %}

