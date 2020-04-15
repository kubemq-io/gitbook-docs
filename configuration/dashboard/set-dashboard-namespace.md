# Set Dashboard Namespace

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --namespace | string | "kubemq" | set kubemq dashboard namespace |

## Example

Set implicit Kubemq dashboard namespace installation:

```bash
kubemqctl create dashboard --namespace kubemq-namespace
```
{% endtab %}

{% tab title="Helm" %}
## Values

No values defined for dashboard namespace.

## Example

Set implicit Kubemq dashboard namespace installation:

```bash
helm install kubemq-dashboard  kubemq-charts/dashboard -n kubemq-dashboard-namesapce
```
{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| namespace | string | "kubemq-dashboard" | set kubemq dashboard namespace |

## Example

Set implicit Kubemq dashboard namespace installation:

Run:

```bash
kubectl apply -f {below-yaml-file}
```

```yaml
apiVersion: core.k8s.kubemq.io/v1alpha1
kind: KubemqDashboard
metadata:
  name: kubemq-dashboard
  namesapce: kubemq-dashboard-namespace
```
{% endtab %}
{% endtabs %}

