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
helm install kubemq-operator kubemq-charts/operator
```

## Install KubeMQ Targets Connector

```bash
helm install kubemq-targets kubemq-charts/connector --set type=targets
```

## Install KubeMQ Sources Connector

```bash
helm install kubemq-sources kubemq-charts/connector --set type=sources
```

## Install KubeMQ Bridges Connector

```bash
helm install kubemq-bridges kubemq-charts/connector --set type=bridges
```

