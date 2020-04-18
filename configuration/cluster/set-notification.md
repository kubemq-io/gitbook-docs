# Set Notification

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --notification-enabled | bool | false | Enable notification configuration |
| --notification-prefix | string | "" | Set notification channel prefix |
| --notification-log | bool | false | Set log notification to stdout" |

## Example

Send notifications to notification prefix channel:

```bash
kubemqctl create cluster --notification-enabled --notification-prefix notification
```
{% endtab %}

{% tab title="Helm" %}
## Values

| Value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| notification.enabled | bool | false | Enable notification configuration |
| notification.prefix | string | "" | Set notification channel prefix |
| notification.log | bool | false | Set log notification to stdout" |

## Example

Send notifications to notification prefix channel:

```bash
helm install kubemq-cluster --set notification.enabled=true,notification.prefix=notification  kubemq-charts/kubemq
```
{% endtab %}

{% tab title="yaml" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| enabled | bool | false | Enable notification configuration |
| prefix | string | "" | Set notification channel prefix |
| log | bool | false | Set log notification to stdout" |

## Example

Send notifications to notification prefix channel:

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
  notification:
    enabled: true
    prefix: notification
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
[Learn Access Control - Notification Feature](https://github.com/kubemq-io/gitbook-docs/tree/864b0902d11420db7eced111d8cf9e295a654a6e/learn/access-control/notification.md)
{% endhint %}

