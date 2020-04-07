# Set Health Probe

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --health-enabled | bool | false | Set enable/disable health prob |
| --initial-delay-seconds | int | 10 | Set Initial Delay Seconds |
| --health-period-seconds | int | 10 | Set Period Seconds Interval |
| --health-timeout-seconds | int | 5 | Set Timeout Seconds |
| --health-success-threshold | int | 1 | Set Success Threshold |
| --health-failure-threshold | int | 12 | Set Failure Threshold |

## Example

Enable liveness prob with default values

```bash
kubemqctl create cluster --health-enabled true
```

Change default of visibility to 3 minutes:

```bash
kubemqctl create cluster --queue-default-visibility-seconds 180
```
{% endtab %}

{% tab title="Helm" %}
## Values

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| health.enabled | bool | false | Set enable/disable health prob |
| health.initialDelaySeconds | int | 10 | Set Initial Delay Seconds |
| health.periodSeconds | int | 10 | Set Period Seconds Interval |
| health.timeoutSeconds | int | 5 | Set Timeout Seconds |
| health.successThreshold | int | 1 | Set Success Threshold |
| health.failureThreshold | int | 12 | Set Failure Threshold |

## Example

Enable liveness prob with default values

```bash
helm install kubemq-cluster  --set health.enabled=true  kubemq-charts/kubemq
```
{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| enabled | bool | false | Set enable/disable health prob |
| initialDelaySeconds | int | 10 | Set Initial Delay Seconds |
| periodSeconds | int | 10 | Set Period Seconds Interval |
| timeoutSeconds | int | 5 | Set Timeout Seconds |
| successThreshold | int | 1 | Set Success Threshold |
| failureThreshold | int | 12 | Set Failure Threshold |

## Example

Enable liveness prob with default values

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
  health:
    enabled: false
    initialDelaySeconds: 5
    periodSeconds: 10
    timeoutSeconds: 10
    failureThreshold: 12
    successThreshold: 1
```
{% endtab %}
{% endtabs %}

