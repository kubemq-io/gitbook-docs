# Set Logs

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --log-level | int | 2 | Set log level, 1 - debug , 2 - info, 3 - warn, 4 - error, 5 - fatal |
| --log-file | string | "" | Set log file write path |

## Example

Set debug level:

```bash
kubemqctl create cluster --log-level 1
```
{% endtab %}

{% tab title="Helm" %}
## Values

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| log.level | int | 2 | Set log level, 1 - debug , 2 - info, 3 - warn, 4 - error, 5 - fatal |
| log.file | string | "" | Set log file write path |

## Example

Set debug level:

```bash
helm install kubemq-cluster  --set log.level=1  kubemq-charts/kubemq
```
{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| level | int | 2 | Set log level, 1 - debug , 2 - info, 3 - warn, 4 - error, 5 - fatal |
| file | string | "" | Set log file write path |

## Example

Set debug level:

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
  log:
    level: 1
```
{% endtab %}
{% endtabs %}

