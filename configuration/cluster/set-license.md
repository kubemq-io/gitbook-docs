# Set License

Create Kubemq Cluster with Enterprise License

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --license-data | string | "" | Set license data |
| --license-file | string | "" | set license filename |
| --license-token | string | "" | Set license token" |

## Examples

With license token:

```bash
kubemqctl create cluster -t {your-license-token-here}
```

With license key file:

```bash
kubemqctl create cluster --license-file ./license.key
```

Where license.key contains the license data
{% endtab %}

{% tab title="Helm" %}
## Values

| Value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| license | string | "" | Set license data |

## Example

With license key file:

```bash
helm install kubemq-cluster --set-file license=./license.key
```

Where license.key contains the license data
{% endtab %}

{% tab title="yaml" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| license | string | "" | Set license data |

## Example

With license key data:

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
  license: |-
    { License Data Here}
```
{% endtab %}
{% endtabs %}

