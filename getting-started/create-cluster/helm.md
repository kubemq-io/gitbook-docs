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

## Configuration

The following values yaml lists the configurable parameters of the KubeMQ cluster chart and their default values.

{% file src="../../.gitbook/assets/cluster-values.yaml" caption="values.yaml" %}

```yaml
configData: ""
replicas: 3
volume:
  size: ""
license:
  data: ""
  token: ""
image:
  image: "docker.io/kubemq/kubemq:latest"
  pullPolicy: Always
api:
  disabled: false
  port: 8080
  expose: ClusterIP
  nodePort: 0
grpc:
  disabled: false
  port: 50000
  expose: ClusterIP
  nodePort: 0
  bodyLimit: 0
  bufferSize: 0
rest:
  disabled: false
  port: 9090
  expose: ClusterIP
  nodePort: 0
  bodyLimit: 0
  bufferSize: 0
tls:
  cert: ""
  key: ""
  ca: ""
resources:
  enable: false
  limits:
    cpu: 500m
    memory: 512Mi
  requests:
    cpu: 100m
    memory: 256Mi
nodeSelectors:
  keys: {}
authentication:
  key: ""
  type: ""
authorization:
  policyData: ""
  url: ""
  autoReload: 0
health:
  enabled: false
  initialDelaySeconds: 4
  periodSeconds: 10
  timeoutSeconds: 5
  failureThreshold: 6
  successThreshold: 1
routing:
  data: ""
  url: ""
  autoReload: 0
log:
  level: 2
  file: ""
notification:
  enabled: false
  prefix: ""
  log: false
store:
  clean: false
  path: "./store"
  maxChannels: 0
  maxSubscribers: 0
  maxMessages: 0
  maxChannelSize: 0
  messagesRetentionMinutes: 1440
  purgeInactiveMinutes: 1440
queue:
  maxReceiveMessagesRequest: 1024
  maxWaitTimeoutSeconds: 3600
  maxExpirationSeconds: 43200
  maxDelaySeconds: 43200
  maxReQueues: 1024
  maxVisibilitySeconds: 43200
  defaultVisibilitySeconds: 60
  defaultWaitTimeoutSeconds: 1
gateways:
  remotes: []
  port: 7000
  cert: ""
  key: ""
  ca: ""
```

{% page-ref page="../../configuration/cluster.md" %}

