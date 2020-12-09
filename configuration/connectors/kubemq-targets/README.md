# KubeMQ Targets

## Targets

### Standalone Services

| Category   | Target                                                              | Kind                  | Configuration                        |
|:-----------|:--------------------------------------------------------------------|:----------------------|:-------------------------------------|
| Cache      |                                                                     |                       |                                      |
|            | [Redis](https://redis.io/)                                          | cache.redis           | [Usage](stand-alone/redis.md)         |
|            | [Memcached](https://memcached.org/)                                 | cache.memcached       | [Usage](stand-alone/memcached.md)     |
|            | [Hazelcast](https://hazelcast.com/)                                 | cache.hazelcast       | [Usage](./stand-alone/hazelcast.md)     |
| Stores/db  |                                                                     |                       |                                      |
|            | [Postgres](https://www.postgresql.org/)                             | stores.postgres       | [Usage](./stand-alone/postgres.md)     |
|            | [Mysql](https://www.mysql.com/)                                     | stores.mysql          | [Usage](./stand-alone/mysql.md)        |
|            | [MSSql](https://www.microsoft.com/en-us/sql-server/sql-server-2019) | stores.mssql          | [Usage](./stand-alone/mssql.md)        |
|            | [MongoDB](https://www.mongodb.com/)                                 | stores.mongodb        | [Usage](./stand-alone/mongodb.md)      |
|            | [Elastic Search](https://www.elastic.co/)                           | stores.elastic-search | [Usage](./stand-alone/elastic.md)      |
|            | [Cassandra](https://cassandra.apache.org/)                          | stores.cassandra      | [Usage](./stand-alone/cassandra.md)    |
|            | [Couchbase](https://www.couchbase.com/)                             | stores.couchbase      | [Usage](./stand-alone/couchbase.md)    |
|            | [CockroachDB](https://www.cockroachlabs.com/)                             | stores.cockroach      | [Usage](./stand-alone/cockroachdb.md)    |
| Messaging  |                                                                     |                       |                                      |
|            | [Kafka](https://kafka.apache.org/)                                  | messaging.kafka       | [Usage](./stand-alone/kafka.md)     |
|            | [Nats](https://nats.io/)                                            | messaging.nats        | [Usage](./stand-alone/nats.md)      |
|            | [RabbitMQ](https://www.rabbitmq.com/)                               | messaging.rabbitmq    | [Usage](./stand-alone/rabbitmq.md)  |
|            | [MQTT](http://mqtt.org/)                                            | messaging.mqtt        | [Usage](./stand-alone/mqtt.md)      |
|            | [ActiveMQ](http://activemq.apache.org/)                             | messaging.activemq    | [Usage](./stand-alone/activemq.md)  |
|            | [IBM-MQ](https://developer.ibm.com/components/ibm-mq)               | messaging.ibmmq       | [Usage](./stand-alone/ibmmq.md)     |
| Storage    |                                                                     |                       |                                      |
|            | [Minio/S3](https://min.io/)                                         | storage.minio         | [Usage](./stand-alone/minio.md)       |
| Serverless |                                                                     |                       |                                      |
|            | [OpenFaas](https://www.openfaas.com/)                               | serverless.openfaas   | [Usage](./stand-alone/openfass.md) |
| Http       |                                                                     |                       |                                      |
|            | Http                                                                | http                  | [Usage](./stand-alone/http.md)                |

