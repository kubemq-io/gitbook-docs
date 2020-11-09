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

## Install KubeMQ Cluster Community Edition

```bash
helm install kubemq-cluster kubemq-charts/kubemq
```

## Install KubeMQ Cluster Enterprise Edition

Save your key to a file \(e.g. ./lic.key\)

```bash
helm install kubemq-cluster --set-file license=./lic.key -n kubemq kubemq-charts/kubemq
```

## Configuration

Check out cluster configuration setting available:

{% page-ref page="../../configuration/cluster/" %}

