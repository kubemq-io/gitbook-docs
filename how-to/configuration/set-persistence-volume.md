# Set Persistent Volume

## Set Volume Size

Create Kubemq Cluster with 30Gi Persistent Volume Claim

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster -v 30Gi
```
{% endtab %}

{% tab title="Helm" %}
```bash
helm install kubemq-cluster --set volume.size=30Gi -n kubemq kubemq-charts/kubemq
```
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
  volume:
    size: 30Gi
```
{% endtab %}
{% endtabs %}

## Set Storage Class

Create Kubemq Cluster with 30Gi Persistent Volume Claim with specific Storage Class name

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster -v 30Gi --volume-storage-class "your-storage-class-name"
```
{% endtab %}

{% tab title="Helm" %}
```bash
helm install kubemq-cluster --set volume.size=30Gi,volume.storageClass="your-storage-class-name" -n kubemq kubemq-charts/kubemq
```
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
  volume:
    size: 30Gi
    storageClass: "your-storage-class-name"
```
{% endtab %}
{% endtabs %}

