# Helm

KubeMQ Helm charts required Helm v3. Please download/upgrade from [https://github.com/helm/helm](https://github.com/helm/helm)

## Add KubeMQ Helm Repository

```bash
helm repo add kubemq-charts  https://kubemq-io.github.io/charts
```

## Update KubeMQ Helm Repository

```bash
helm repo update
```

## Install KubeMQ Cluster

```bash
helm install kubemq-cluster --set key={your-license-key} kubemq-charts/kubemq -n kubemq --create-namespace --wait
```



## Configuration

Check out cluster configuration setting available:

{% content-ref url="../../configuration/cluster/" %}
[cluster](../../configuration/cluster/)
{% endcontent-ref %}
