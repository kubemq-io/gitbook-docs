# Set View Port

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --port | int |  | set kubemq dashboard expose port view |

## Example

Set dashboard view to port 32000

```bash
kubemqctl create dashboard --port 32000
```
{% endtab %}

{% tab title="Helm" %}
## Values

| Value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| port | int |  | set kubemq dashboard expose port view |

## Example

Set dashboard view to port 32000

```bash
helm install kubemq-dashboard  --set port=32000 kubemq-charts/dashboard
```
{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| port | int |  | set kubemq dashboard expose port view |

## Example

Set dashboard view to port 32000:

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
  port: 33200
```
{% endtab %}
{% endtabs %}

