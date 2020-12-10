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
