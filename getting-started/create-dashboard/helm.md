# Helm

KubeMQ Helm charts required Helm v3. Please download/upgrade from [https://github.com/helm/helm](https://github.com/helm/helm)

Add KubeMQ Helm Repository:
```
helm repo add kubemq-charts  https://kubemq-io.github.io/charts
```

Verify kubemq helm repository charts is properly configured by:

```
helm repo list
```

Install KubeMQ Chart:

```bash
helm install kubemq-dashboard kubemq-charts/dashboard
```

