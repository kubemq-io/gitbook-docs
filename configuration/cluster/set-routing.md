# Set Routing

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --routing-data | string | "" | Set routing data |
| --routing-file | string | "" | set routing  file |
| --routing-url | string url | "" | Set routing data loading url |
| --routing-auto-reload | int | 0 | Set auto reload routing data from url |

## Example

Set predefined routing rules data where routing.json is json array of routing rules:

```bash
kubemqctl create cluster --routing-file ./routing.json
```

{% endtab %}

{% tab title="Helm" %}
## Values

| Value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| routing.data | string | "" | Set routing data |
| routing.url | string url | "" | Set routing data loading url |
| routing.autoReload | int | 0 | Set auto reload routing data from url |

## Example

Set predefined routing rules data where routing.json is json array of routing rules:

```bash
helm install kubemq-cluster --set-file routing.data=./routing.json kubemq-charts/kubemq
```

{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| data | string | "" | Set routing data |
| url | string url | "" | Set routing data loading url |
| autoReload | int | 0 | Set auto reload routing data from url |

## Example

Set predefined routing rules data where routing.json is json array of routing rules:

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
  authorization:
    data: |-
      [
         {
            "Key":"all-to-foo-bar",
            "Routes": "events:foo.bar;events_store:foo.bar;queues:foo.bar"
         },
         {
            "Key":"sink-to-events-channel",
            "Routes": "events:sink"
         }
      ]
```

{% endtab %}
{% endtabs %}

