# Set Queues Settings


Queues options allows to configure Kubemq Queues defaults.

{% tabs %}
{% tab title="Kubemqctl" %}

#### Flags

| Flag                               | Type/Options | Default | Description                                                         |
|:-----------------------------------|:-------------|:--------|:--------------------------------------------------------------------|
| --queue-max-receive-messages-request | int          | 1024    | Set max of sending / receiving batch of queue message               |
| --queue-max-wait-timeout-seconds     | int          | 3600    | Set max wait timeout allowed for message                             |
| --queue-max-expiration-seconds       | int          | 43200   | Set max expiration allowed for message                              |
| --queue-max-delay-seconds            | int          | 43200   | set max delay seconds allowed for message                           |
| --queue-max-requeue                  | int          | 1024    | Set max retires to receive message before discard                   |
| --queue-max-visibility-seconds       | int          | 43200   | Set max time of hold received message before returning to queue     |
| --queue-default-visibility-seconds   | int          | 60      | Set default time of hold received message before returning to queue |
|-- queue-default-wait-timeout-seconds | int          | 1       | Set default time to wait for a message in a queue                   |



#### Exmaples

Set max delay seconds allowed to no more than one hour:

```bash
kubemqctl create cluster --queue-max-delay-seconds 3600
```

Change default of visibility to 3 minutes:

```bash
kubemqctl create cluster --queue-default-visibility-seconds 180
```
{% endtab %}


{% tab title="Helm" %}

#### Values



| Flag                      | Type/Options | Default | Description                                                         |
|:--------------------------|:-------------|:--------|:--------------------------------------------------------------------|
| queue.maxReceiveMessagesRequest | int          | 1024    | Set max of sending / receiving batch of queue message               |
| queue.maxWaitTimeoutSeconds     | int          | 3600        | Set max wait timeout allowed for message                              |
| queue.maxExpirationSeconds      | int          | 43200        | Set max expiration allowed for message                              |
| queue.maxDelaySeconds           | int          | 43200        | set max delay seconds allowed for message                           |
| queue.maxReQueues               | int          | 1024        | Set max retires to receive message before discard                   |
| queue.maxVisibilitySeconds      | int          | 43200        | Set max time of hold received message before returning to queue     |
| queue.defaultVisibilitySeconds  | int          | 60        | Set default time of hold received message before returning to queue |
| queue.defaultWaitTimeoutSeconds | int          | 1        | Set default time to wait for a message in a queue                   |


#### Exmaples

Set max delay seconds allowed to no more than one hour:

```bash
helm install kubemq-cluster  --set queue.maxDelaySeconds=3600 kubemq-charts/kubemq
```

Change default of visibility to 3 minutes:

```bash
helm install kubemq-cluster  --set queue.defaultVisibilitySeconds=180 kubemq-charts/kubemq
```

{% endtab %}

{% tab title="kubectl" %}

#### Fields


| Flag                      | Type/Options | Default | Description                                                         |
|:--------------------------|:-------------|:--------|:--------------------------------------------------------------------|
| maxReceiveMessagesRequest | int          | 1024    | Set max of sending / receiving batch of queue message               |
| maxWaitTimeoutSeconds     | int          | 3600        | Set max wait timeout allowed for message                              |
| maxExpirationSeconds      | int          | 43200        | Set max expiration allowed for message                              |
| maxDelaySeconds           | int          | 43200        | set max delay seconds allowed for message                           |
| maxReQueues               | int          | 1024        | Set max retires to receive message before discard                   |
| maxVisibilitySeconds      | int          | 43200        | Set max time of hold received message before returning to queue     |
| defaultVisibilitySeconds  | int          | 60        | Set default time of hold received message before returning to queue |
| defaultWaitTimeoutSeconds | int          | 1        | Set default time to wait for a message in a queue                   |


#### Exmaples

Set max delay seconds allowed to no more than one hour:

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
  queue:
    maxDelaySeconds: 3600
```

Change default of visibility to 3 minutes:

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
  queue:
    defaultVisibilitySeconds: 180
```
{% endtab %}
{% endtabs %}




