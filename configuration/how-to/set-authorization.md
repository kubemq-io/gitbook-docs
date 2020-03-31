# Set Authorization

## Set Predefined Authorization Rules Policy

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --authorization-enabled --authorization-policy-file ./policy.json
```

Where policy.json is json array of access control rules.
{% endtab %}

{% tab title="Helm" %}
```bash
helm install kubemq-cluster --set-file authorization.policyData=./policy.json kubemq-charts/kubemq
```

Where policy.json is json array of access control rules.
{% endtab %}

{% tab title="yaml" %}
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
  policy: |-
    [
       {
          "ClientID":"client-1",
          "Events":true,
          "EventsStore": false,
          "Queues": false,
          "Commands": false,
          "Queries": false,
          "Channel":"foo.bar.1",
          "Read":false,
          "Write": true
       },
       {
          "ClientID":"client-2",
          "Events":true,
          "EventsStore": false,
          "Queues": false,
          "Commands": false,
          "Queries": false,
          "Channel":"foo.bar.2",
          "Read":false,
          "Write": true
       },
    ]
```
{% endtab %}
{% endtabs %}

## Set Authorization Web Service Rules Source

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --authorization-enabled --authorization-url "http://your.url.rules/" --authorization-auto-reload 120
```

Kubemq will call "[http://your.url.rules](http://your.url.rules)" every 120 seconds and pulls the Authorization policy json array
{% endtab %}

{% tab title="Helm" %}
```bash
helm install kubemq-cluster --set authorization.url="http://your.url.rules/",authorization.autoReload=120 kubemq-charts/kubemq
```

Kubemq will call "[http://your.url.rules](http://your.url.rules)" every 120 seconds and pulls the Authorization policy json array
{% endtab %}

{% tab title="yaml" %}
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
  url: "http://your.url.rules/"
  autoReload: 120
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
[Learn Access Control - Authorization Feature](../../learn/access-control/authorization.md)
{% endhint %}

