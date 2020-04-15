# Set Grafana Image

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --grafana-image | string | grafana/grafana:latest | set kubemq dashboard grafana docker image |

## Example

Set dashboard grafana image to specific image

```bash
kubemqctl create dashboard --grafana-image grafana-image-name:
```
{% endtab %}

{% tab title="Helm" %}
## Values

| Value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| grafana.image | string | grafana/grafana:latest | set kubemq dashboard grafana docker image |

## Example

Set dashboard grafana image to specific image:

```bash
helm install kubemq-dashboard  --set grafana.image=grafana-image-name kubemq-charts/dashboard
```
{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| image | string | grafana/grafana:latest | set kubemq dashboard grafana docker image |

## Example

Set dashboard grafana image to specific image:

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
  grafana:
    image: grafana-image-name
```
{% endtab %}
{% endtabs %}

