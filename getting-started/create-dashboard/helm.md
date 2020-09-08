# Helm

KubeMQ Helm charts required Helm v3. Please download/upgrade from [https://github.com/helm/helm](https://github.com/helm/helm)

## Add KubeMQ Helm Repository

```text
helm repo add kubemq-charts  https://kubemq-io.github.io/charts
```

## Update KubeMQ Helm Repository

```bash
helm repo update
```

## Install KubeMQ Operator

```bash
helm install kubemq-operator kubemq-charts/operator
```

## Install KubeMQ Dashboard

```bash
helm install kubemq-dashboard kubemq-charts/dashboard
```

## Configuration

Check out  dashboard configuration setting available:

{% page-ref page="../../configuration/dashboard/" %}

