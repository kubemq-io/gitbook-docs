# Set Enterprise License

Create Kubemq Cluster with Enterprise License

{% tabs %}
{% tab title="Kubemqctl" %}

#### With License Token
```bash
kubemqctl create cluster -t {your-license-token-here}
```
{% endtab %}

#### With License Key

```bash
kubemqctl create cluster --license-filename ./license.key
```
Where license.key contains the license data
{% endtab %}

{% tab title="Helm" %}

```bash
helm install kubemq-cluster --set-file license=./license.key
```
Where license.key contains the license data

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
  license: |-
    { License Data Here} 
```
{% endtab %}
{% endtabs %}

