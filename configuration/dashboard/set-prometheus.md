# Set Prometheus Image

{% tabs %}
{% tab title="Kubemqctl" %}

## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --prometheus-image | string |  prometheus/prometheus:latest| set kubemq dashboard prometheus docker image|

## Example

Set dashboard prometheus image to specific image

```bash
kubemqctl create dashboard --prometheus-image prometheus-image-name:
```
{% endtab %}

{% tab title="Helm" %}
## Values

| Value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| prometheus.image | string |  prometheus/prometheus:latest| set kubemq dashboard prometheus docker image|

## Example

Set dashboard prometheus image to specific image:

```bash
helm install kubemq-dashboard  --set prometheus.image=prometheus-image-name kubemq-charts/dashboard
```
{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| image | string |  prometheus/prometheus:latest| set kubemq dashboard prometheus docker image|

## Example


Set dashboard prometheus image to specific image:

Run:

```bash
kubectl apply -f {below-yaml-file}
```

```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqDashboard
metadata:
  name: kubemq-dashboard
  namesapce: kubemq
spec:
  prometheus:
    image: prometheus-image-name
```
{% endtab %}
{% endtabs %}

