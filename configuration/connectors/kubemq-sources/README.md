# KubeMQ Sources

## Sources


### Standalone Services

| Category  | Target                                                | Kind               | Configuration                       |
|:----------|:------------------------------------------------------|:-------------------|:------------------------------------|
| Http      | Http                                                  | http               | [Usage](./http.md)               |
| Messaging |                                                       |                    |                                     |
|           | [Kafka](https://kafka.apache.org/)                    | messaging.kafka    | [Usage](messaging/kafka.md)    |
|           | [RabbitMQ](https://www.rabbitmq.com/)                 | messaging.rabbitmq | [Usage](messaging/rabbitmq.md) |
|           | [MQTT](http://mqtt.org/)                              | messaging.mqtt     | [Usage](messaging/mqtt.md)     |
|           | [ActiveMQ](http://activemq.apache.org/)               | messaging.activemq | [Usage](messaging/activemq.md) |
|           | [IBM-MQ](https://developer.ibm.com/components/ibm-mq) | messaging.ibmmq    | [Usage](messaging/ibmmq.md)    |
|           | [Nats](https://nats.io/)                              | messaging.nats     | [Usage](messaging/nats.md)     |


### Google Cloud Platform (GCP)

| Category  | Target                                     | Kind       | Configuration               |
|:----------|:-------------------------------------------|:-----------|:----------------------------|
| Messaging | [Pub/Sub](https://cloud.google.com/pubsub) | gcp.pubsub | [Usage](./gcp/pubsub.md) |

### Amazon Web Service (AWS)


| Category  | Target                                        | Kind         | Configuration                 |
|:----------|:----------------------------------------------|:-------------|:------------------------------|
| Messaging |                                               |              |                               |
|           | [AmazonMQ](https://aws.amazon.com/amazon-mq/) | aws.amazonmq | [Usage](./aws/amazonmq.md) |
|           | [MSK](https://aws.amazon.com/msk/)            | aws.msk      | [Usage](./aws/msk.md)      |
|           | [SQS](https://aws.amazon.com/sqs/)            | aws.sqs      | [Usage](./aws/sqs.md)      |

### Microsoft Azure

| Category   | Target                                                                | Kind             | Configuration                     |
|:-----------|:----------------------------------------------------------------------|:-----------------|:----------------------------------|
| EventHubs  |                                                                       |                  |                                   |
|            | [EventHubs](https://azure.microsoft.com/en-us/services/event-hubs/)   | azure.eventhubs  | [Usage](./azure/eventhubs.md)  |
| ServiceBus |                                                                       |                  |                                   |
|            | [ServiceBus](https://azure.microsoft.com/en-us/services/service-bus/) | azure.servicebus | [Usage](./azure/servicebus.md) |

## Targets

| Type                                                                              | Kind                | Configuration                           |
|:----------------------------------------------------------------------------------|:--------------------|:----------------------------------------|
| [Queue](https://docs.kubemq.io/learn/message-patterns/queue)                      | kubemq.queue        | [Usage](./targets/queue.md)        |
| [Events](https://docs.kubemq.io/learn/message-patterns/pubsub#events)             | kubemq.events       | [Usage](./targets/events.md)       |
| [Events Store](https://docs.kubemq.io/learn/message-patterns/pubsub#events-store) | kubemq.events-store | [Usage](./targets/events-store.md) |
| [Command](https://docs.kubemq.io/learn/message-patterns/rpc#commands)             | kubemq.command      | [Usage](./targets/command.md)      |
| [Query](https://docs.kubemq.io/learn/message-patterns/rpc#queries)                | kubemq.query        | [Usage](./targets/query.md)        |


## Middlewares 

In bindings configuration, KubeMQ Bridges supports middleware setting for each pair of source and target bindings.

These properties contain middleware information settings as follows:

### Logs Middleware

KubeMQ Bridges supports level based logging to console according to as follows:

| Property  | Description       | Possible Values        |
|:----------|:------------------|:-----------------------|
| log_level | log level setting | "debug","info","error" |
|           |                   |  "" - indicate no logging on this bindings |

An example for only error level log to console:

```yaml
bindings:
  - name: sample-binding 
    properties: 
      log_level: error
    sources:
    ......  
```

### Retry Middleware

KubeMQ Bridges supports Retries' target execution before reporting of error back to the source on failed execution.

Retry middleware settings values:


| Property                      | Description                                           | Possible Values                             |
|:------------------------------|:------------------------------------------------------|:--------------------------------------------|
| retry_attempts                | how many retries before giving up on target execution | default - 1, or any int number              |
| retry_delay_milliseconds      | how long to wait between retries in milliseconds      | default - 100ms or any int number           |
| retry_max_jitter_milliseconds | max delay jitter between retries                      | default - 100ms or any int number           |
| retry_delay_type              | type of retry delay                                   | "back-off" - delay increase on each attempt |
|                               |                                                       | "fixed" - fixed time delay                  |
|                               |                                                       | "random" - random time delay                |

An example for 3 retries with back-off strategy:

```yaml
bindings:
  - name: sample-binding 
    properties: 
      retry_attempts: 3
      retry_delay_milliseconds: 1000
      retry_max_jitter_milliseconds: 100
      retry_delay_type: "back-off"
    sources:
    ......  
```
