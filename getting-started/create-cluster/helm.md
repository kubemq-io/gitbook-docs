# Helm

KubeMQ Helm charts required Helm v3. Please download/upgrade from [https://github.com/helm/helm](https://github.com/helm/helm)

## Add KubeMQ Helm Repository

```text
helm repo add kubemq-charts  https://kubemq-io.github.io/charts
```

## Verify KubeMQ Helm Repository Charts

```text
helm repo list
```

## Install KubeMQ Cluster

```bash
helm install kubemq-cluster kubemq-charts/kubemq
```

