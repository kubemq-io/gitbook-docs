# Set Authorization


{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag                      | Type/Options | Default | Description                          |
|:--------------------------|:-------------|:--------|:-------------------------------------|
| --authorization-enabled     | string       | false   | Enable authorization configuration   |
| --authorization-policy-data | string       | ""      | Set authorization policy data        |
| --authorization-policy-file | string       | ""      | set authorization policy filename    |
| --authorization-url         | string url   | ""      | Set authorization policy loading url |
| --authorization-auto-reload | int          | 0       | Set auto reload policy data from url |

## Exmaples

Set predefined authorization rules policy where policy.json is json array of access control rules:

```bash
kubemqctl create cluster --authorization-enabled --authorization-policy-file ./policy.json
```
.

Set authorization web service rules source:

```bash
kubemqctl create cluster --authorization-enabled --authorization-url "http://your.url.rules/" --authorization-auto-reload 120
```

Kubemq will call "[http://your.url.rules](http://your.url.rules)" every 120 seconds and pulls the Authorization policy json array


{% endtab %}

{% tab title="Helm" %}
## Values

| Flag                     | Type/Options | Default | Description                                           |
|:-------------------------|:-------------|:--------|:------------------------------------------------------|
| authorization.PolicyData | string       |     ""    | Set Authorization policy data                         |
| authorization.url        | string url   |   ""      | Set Optional authorization server url for policy data |
| authorization.autoReload | int          |     0    | Set auto reload policy data from url                  |


## Exmaples

Set predefined authorization rules policy where policy.json is json array of access control rules:

```bash
helm install kubemq-cluster --set-file authorization.policyData=./policy.json kubemq-charts/kubemq
```


Set authorization web service rules source:

```bash
helm install kubemq-cluster --set authorization.url="http://your.url.rules/",authorization.autoReload=120 kubemq-charts/kubemq
```

{% endtab %}

{% tab title="kubectl" %}
## Fields

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| policyData | string | ""|Set Authorization policy data |
| url | string url |"" |Set Optional authorization server url for policy data |
| autoReload | int |0 |Set auto reload policy data from url |

## Exmaples

Set predefined authorization rules policy where policy.json is json array of access control rules:

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


Set authorization web service rules source:

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
    url: "http://your.url.rules/"
    autoReload: 120
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
[Learn Access Control - Authorization Feature](../../learn/access-control/authorization.md)
{% endhint %}

