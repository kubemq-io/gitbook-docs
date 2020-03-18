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

## Install KubeMQ Dashboard

```bash
helm install kubemq-dashboard kubemq-charts/dashboard
```

## Configuration

The following table lists the configurable parameters of the KubeMQ dashboard chart and their default values.

{% file src="../../.gitbook/assets/dashboard-values.yaml" caption="values.yaml" %}

```yaml
port: 32000
prometheus:
  nodePort: 0
  image: prom/prometheus:latest
grafana:
  image: grafana/grafana:latest
  dashboardUrl: "https://raw.githubusercontent.com/kubemq-io/kubemq-dashboard/master/dashboard.json"
```

{% page-ref page="../../configuration/dashboard.md" %}

