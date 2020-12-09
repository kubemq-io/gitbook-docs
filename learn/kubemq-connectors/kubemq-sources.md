# KubeMQ Sources

KubeMQ Sources connects external systems and cloud services with KubeMQ message queue broker.

KubeMQ Sources allows us to build a message-based microservices architecture on Kubernetes with minimal efforts and without developing connectivity interfaces between external system such as messaging components (RabbitMQ, Kafka, MQTT) ,REST APIs and KubeMQ message queue broker.
In addition, KubeMQ Sources allows migrating legacy systems (together with [KubeMQ Targets](https://github.com/kubemq-hub/kubemq-targets)) to KubeMQ based messaging architecture.


**Key Features**:

- **Runs anywhere**  - Kubernetes, Cloud, on-prem, anywhere
- **Stand-alone** - small docker container / binary
- **Single Interface** - One interface all the services
- **API Gateway** - Act as an REST Api gateway
- **Plug-in Architecture** Easy to extend, easy to connect
- **Middleware Supports** - Logs, Metrics, Retries, and Rate Limiters
- **Easy Configuration** - simple yaml file builds your topology

## Concepts

KubeMQ Sources building blocks are:
 - Binding
 - Source
 - Target

### Binding

Binding is a 1:1 connection between Source and Target. Every Binding runs independently.

![binding](../../.gitbook/assets/learn-kubemq-sources-binding.jpg)

### Source

Source is an external service that provide ingress data to KubeMQ's channels which then later consumed by services connected to KubeMQ server.

Source can be services such HTTP REST Api, Messaging systems (RabbitMQ, Kafka, MQTT etc).

KubeMQ Sources integrate each one of the supported sources and ingest data into KubeMQ via Targets.


### Target

The target is a KubeMQ connection which send the data from the sources and route them to the appropriate KubeMQ channel for action, and return back a response if needed.
