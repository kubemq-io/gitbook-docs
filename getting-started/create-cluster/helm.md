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

## Install KubeMQ Operator

```bash
helm install kubemq-operator kubemq-charts/operator -n kubemq
```

## Install KubeMQ Cluster

```bash
helm install kubemq-cluster --set key={your-license-key} kubemq-charts/kubemq -n kubemq 
```



## Configuration

Check out cluster configuration setting available:

{% page-ref page="../../configuration/cluster/" %}

