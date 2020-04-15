# Set Dashboard Name

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --name | string | "kubemq-dashboard" | set kubemq dashboard name |

## Example

Set implicit Kubemq dashboard name:

```bash
kubemqctl create dashboard --name your-kubemq-dashboard-name
```
{% endtab %}

{% tab title="Helm" %}
## Values

No values defined for dashboard name.

## Example

Set implicit Kubemq dashboard name:

```bash
helm install your-kubemq-dashboard-name  kubemq-charts/dashboard
```
{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| name | string | "kubemq-dashboard" | set kubemq dashboard name |

## Example

Set implicit Kubemq dashboard name:

Run:

```bash
kubectl apply -f {below-yaml-file}
```

```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqDashboard
metadata:
  name: your-kubemq-dashboard-name
  namesapce: kubemq
```
{% endtab %}
{% endtabs %}

