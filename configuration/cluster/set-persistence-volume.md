# Set Persistent Volume

## Set Volume Size

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --volume-size | string | "" | Desired size of Persisted Volume Claim |
| --volume-storageClass | string | "default" | Set persisted volume storage class |

## Examples

Create KubeMQ Cluster with 30Gi Persistent Volume Claim:

```bash
kubemqctl create cluster -v 30Gi
```

Create Kubemq Cluster with 30Gi Persistent Volume Claim and specific Storage Class name:

```bash
kubemqctl create cluster -v 30Gi --volume-storage-class "your-storage-class-name"
```
{% endtab %}

{% tab title="Helm" %}
## Values

| Value | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| volume.size | string | "" | Desired size of Persisted Volume Claim |
| volume.storageClass | string | "default" | Set persisted volume storage class |

## Examples

Create Kubemq Cluster with 30Gi Persistent Volume Claim:

```bash
helm install kubemq-cluster --set volume.size=30Gi -n kubemq kubemq-charts/kubemq
```

Create Kubemq Cluster with 30Gi Persistent Volume Claim with specific Storage Class name:

```bash
helm install kubemq-cluster --set volume.size=30Gi,volume.storageClass="your-storage-class-name" -n kubemq kubemq-charts/kubemq
```
{% endtab %}

{% tab title="kubectl" %}
## Fields

| Field | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| size | string | "" | Desired size of Persisted Volume Claim |
| storageClass | string | "default" | Set persisted volume storage class |

## Examples

Create Kubemq Cluster with 30Gi Persistent Volume Claim:

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

Create Kubemq Cluster with 30Gi Persistent Volume Claim with specific Storage Class name:

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

