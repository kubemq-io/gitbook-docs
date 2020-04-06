# Set Cluster Image

{% tabs %}
{% tab title="Kubemqctl" %}
## Flags

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| --image | string |docker.io/kubemq/kubemq-uni:latest| Set kubemq server image |
| --image-pull-policy | string Always/IfNotPresent/Never | Always|Set image pull policy |

## Exmaple

Set implicit Kubemq cluster docker image:

```bash
kubemqctl create cluster --image docker.io/kubemq/kubemq:latest
```
Replace `docker.io/kubemq/kubemq:latest` with the desired image with the `registry/repository:tag` format

{% endtab %}

{% tab title="Helm" %}

## Values

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| image.image | string |docker.io/kubemq/kubemq-uni:latest| Set kubemq server image |
| image.pullPolicy | string Always/IfNotPresent/Never | Always|Set image pull policy |

## Exmaple

Set implicit Kubemq cluster docker image:

```bash
helm install kubemq-cluster  --set image.image  docker.io/kubemq/kubemq:latest kubemq-charts/kubemq
```

Replace `docker.io/kubemq/kubemq:latest` with the desired image with the `registry/repository:tag` format
{% endtab %}

{% tab title="kubectl" %}

## Fields

| Flag | Type/Options | Default | Description |
| :--- | :--- | :--- | :--- |
| image | string |docker.io/kubemq/kubemq-uni:latest| Set kubemq server image |
| pullPolicy | string Always/IfNotPresent/Never | Always|Set image pull policy |

## Exmaple

Set implicit Kubemq cluster docker image:
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
  image:
    image: "docker.io/kubemq/kubemq:latest"
```
{% endtab %}
{% endtabs %}

