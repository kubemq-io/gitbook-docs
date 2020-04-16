# Set Store Settings

Store options allows to configure the way Kubemq server store persistence data for both events\_store and queues message patterns.

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --store-clean | bool | false | Set clear persistence data on start-up |
| --store-path | string | ./store | Set persistence file path |
| --store-max-channels | int | 0 | Set limit number of persistence channels |
| --store-max-subscribers | int | 0 | Set limit of subscribers per channel |
| --store-max-messages | int | 0 | Set limit of messages per channel |
| --store-max-channel-size | int | 0 | Set limit size of channel in bytes |
| --store-messages-retention-minutes | int | 1440 | Set message retention time in minutes |
| --store-purge-inactive-minutes | int | 1440 | Set time in minutes of channel inactivity to delete |

## Examples

Clean store when loading - in case of a need to clean and start fresh store

```bash
kubemqctl create cluster --store-clean true
```

Delete inactive channels after 180 minutes if inactivity

```bash
kubemqctl create cluster --store-purge-inactive-minutes 180
```
{% endtab %}

{% tab title="Helm" %}
## Values

| Value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| store.clean | bool | false | Set clear persistence data on start-up |
| store.path | string | ./store | Set persistence file path |
| store.maxChannels | int | 0 | Set limit number of persistence channels |
| store.maxSubscribers | int | 0 | Set limit of subscribers per channel |
| store.maxMessages | int | 0 | Set limit of messages per channel |
| store.maxChannel-size | int | 0 | Set limit size of channel in bytes |
| store.messagesRetention-minutes | int | 1440 | Set message retention time in minutes |
| store.purgeInactiveMinutes | int | 1440 | Set time in minutes of channel inactivity to delete |

## Examples

Clean store when loading - in case of a need to clean and start fresh store

```bash
helm install kubemq-cluster  --set store.clean=true kubemq-charts/kubemq
```

Delete inactive channels after 180 minutes if inactivity

```bash
helm install kubemq-cluster  --set store.purgeInactiveMinutes=t180 kubemq-charts/kubemq
```
{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| clean | bool | false | Set clear persistence data on start-up |
| path | string | ./store | Set persistence file path |
| maxChannels | int | 0 | Set limit number of persistence channels |
| maxSubscribers | int | 0 | Set limit of subscribers per channel |
| maxMessages | int | 0 | Set limit of messages per channel |
| maxChannel-size | int | 0 | Set limit size of channel in bytes |
| messagesRetention-minutes | int | 1440 | Set message retention time in minutes |
| purgeInactiveMinutes | int | 1440 | Set time in minutes of channel inactivity to delete |

## Examples

Clean store when loading - in case of a need to clean and start fresh store

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
  store:
    clean: true
```

Delete inactive channels after 180 minutes if inactivity

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
  store:
    purgeInactiveMinutes: 180
```
{% endtab %}
{% endtabs %}

