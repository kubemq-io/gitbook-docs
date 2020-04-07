# Set Resources Limits

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --resources-enabled | bool | false | Enable resources configuration |
| --resources-limits-cpu | string | "2" | Set Limits CPU |
| --resources-limits-memory | 2Gi | string | Set Limits Memory |
| --resources-requests-cpu | string | "2" | Set Requests CPU |
| --resources-requests-memory | string | 512M | Set Requests Memory |

## Example

Set Resources limits:

```bash
kubemqctl create cluster --resources-enabled true
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
| resources.enable | bool | false | Enable resources configuration |
| resources.limitsCpu | string | "2" | Set Limits CPU |
| resources.limitsMemory | 2Gi | string | Set Limits Memory |
| resources.requestsCpu | string | "2" | Set Requests CPU |
| resources.requestsMemory | string | 512M | Set Requests Memory |

## Example

Set Resources limits:

```bash
helm install kubemq-cluster  --set resources.enable=true kubemq-charts/kubemq
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
| enable | bool | false | Enable resources configuration |
| limitsCpu | string | "2" | Set Limits CPU |
| limitsMemory | 2Gi | string | Set Limits Memory |
| requestsCpu | string | "2" | Set Requests CPU |
| requestsMemory | string | 512M | Set Requests Memory |

## Example

Set Resources limits:

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
  resources:
    enable: false
    limits:
      cpu: 2
      memory: 2Gi
    requests:
      cpu: 2
      memory: 512Mi
```
{% endtab %}
{% endtabs %}

