# Set Cluster Image

Set implicit Kubemq cluster docker image

{% tabs %}
{% tab title="Kubemqctl" %}
```bash
kubemqctl create cluster --image docker.io/kubemq/kubemq:latest
```

Replace `docker.io/kubemq/kubemq:latest` with the desired image with the `registry/repository:tag` format
{% endtab %}

{% tab title="Helm" %}
```bash
helm install kubemq-cluster  --set image.image  docker.io/kubemq/kubemq:latest kubemq-charts/kubemq
```

Replace `docker.io/kubemq/kubemq:latest` with the desired image with the `registry/repository:tag` format

{% endtab %}

{% tab title="kubectl" %}

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



