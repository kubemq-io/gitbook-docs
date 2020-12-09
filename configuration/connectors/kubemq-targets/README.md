# KubeMQ Targets

## Targets

### Standalone Services

| Category   | Target                                                              | Kind                  | Configuration                        |
|:-----------|:--------------------------------------------------------------------|:----------------------|:-------------------------------------|
| Cache      |                                                                     |                       |                                      |
|            | [Redis](https://redis.io/)                                          | cache.redis           | [Usage](./stand-alone/redis.md)         |
|            | [Memcached](https://memcached.org/)                                 | cache.memcached       | [Usage](./stand-alone/memcached.md)     |
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
|            | [OpenFaas](https://www.openfaas.com/)                               | serverless.openfaas   | [Usage](./stand-alone/openfaas.md) |
| Http       |                                                                     |                       |                                      |
|            | Http                                                                | http                  | [Usage](./stand-alone/http.md)                |



#### Google Cloud Platform (GCP)

| Category   | Target                                                              | Kind                | Configuration                              |
|:-----------|:--------------------------------------------------------------------|:--------------------|:-------------------------------------------|
| Cache      |                                                                     |                     |                                            |
|            | [Redis](https://cloud.google.com/memorystore)                       | gcp.cache.redis     | [Usage](./gcp/redis.md)     |
|            | [Memcached](https://cloud.google.com/memorystore)                   | gcp.cache.memcached | [Usage](./gcp/memcached.md) |
| Stores/db  |                                                                     |                     |                                            |
|            | [Postgres](https://cloud.google.com/sql)                            | gcp.stores.postgres | [Usage](./gcp/postgres.md)          |
|            | [Mysql](https://cloud.google.com/sql)                               | gcp.stores.mysql    | [Usage](./gcp/mysql.md)             |
|            | [BigQuery](https://cloud.google.com/bigquery)                       | gcp.bigquery        | [Usage](./gcp/bigquery.md)              |
|            | [BigTable](https://cloud.google.com/bigtable)                       | gcp.bigtable        | [Usage](./gcp/bigtable.md)              |
|            | [Firestore](https://cloud.google.com/firestore)                     | gcp.firestore       | [Usage](./gcp/firestore.md)             |
|            | [Spanner](https://cloud.google.com/spanner)                         | gcp.spanner         | [Usage](./gcp/spanner.md)               |
|            | [Firebase](https://firebase.google.com/products/realtime-database/) | gcp.firebase        | [Usage](./gcp/firebase.md)              |
| Messaging  |                                                                     |                     |                                            |
|            | [Pub/Sub](https://cloud.google.com/pubsub)                          | gcp.pubsub          | [Usage](./gcp/pubsub.md)                |
| Storage    |                                                                     |                     |                                            |
|            | [Storage](https://cloud.google.com/storage)                         | gcp.storage         | [Usage](./gcp/storage.md)               |
| Serverless |                                                                     |                     |                                            |
|            | [Functions](https://cloud.google.com/functions)                     | gcp.cloudfunctions  | [Usage](./gcp/cloudfunctions.md)        |
|            |                                                                     |                     |                                            |



#### Amazon Web Service (AWS)


| Category   | Target                                                         | Kind                     | Configuration                           |
|:-----------|:---------------------------------------------------------------|:-------------------------|:----------------------------------------|
| Stores/db  |                                                                |                          |                                         |
|            | [Athena](https://docs.aws.amazon.com/athena)                   | aws.athena               | [Usage](./aws/athena.md)             |
|            | [DynamoDB](https://aws.amazon.com/dynamodb/)                   | aws.dynamodb             | [Usage](./aws/dynamodb.md)           |
|            | [Elasticsearch](https://aws.amazon.com/elasticsearch-service/) | aws.elasticsearch        | [Usage](./aws/elasticsearch.md)      |
|            | [KeySpaces](https://docs.aws.amazon.com/keyspaces)             | aws.keyspaces            | [Usage](./aws/keyspaces.md)          |
|            | [MariaDB](https://aws.amazon.com/rds/mariadb/)                 | aws.rds.mariadb          | [Usage](./aws/mariadb.md)        |
|            | [MSSql](https://aws.amazon.com/rds/sqlserver/)                 | aws.rds.mssql            | [Usage](./aws/mssql.md)          |
|            | [MySQL](https://aws.amazon.com/rds/mysql/)                     | aws.rds.mysql            | [Usage](./aws/mysql.md)          |
|            | [Postgres](https://aws.amazon.com/rds/postgresql/)             | aws.rds.postgres         | [Usage](./aws/postgres.md)       |
|            | [RedShift](https://aws.amazon.com/redshift/)                   | aws.rds.redshift         | [Usage](./aws/rds-redshift.md)       |
|            | [RedShiftSVC](https://aws.amazon.com/redshift/)                | aws.rds.redshift.service | [Usage](./aws/redshift.md)           |
| Messaging  |                                                                |                          |                                         |
|            | [AmazonMQ](https://aws.amazon.com/amazon-mq/)                  | aws.amazonmq             | [Usage](./aws/amazonmq.md)           |
|            | [MSK](https://aws.amazon.com/msk/)                             | aws.msk                  | [Usage](./aws/msk.md)                |
|            | [Kinesis](https://aws.amazon.com/kinesis/)                     | aws.kinesis              | [Usage](./aws/kinesis.md)            |
|            | [SQS](https://aws.amazon.com/sqs/)                             | aws.sqs                  | [Usage](./aws/sqs.md)                |
|            | [SNS](https://aws.amazon.com/sns/)                             | aws.sns                  | [Usage](./aws/sns.md)                |
| Storage    |                                                                |                          |                                         |
|            | [S3](https://aws.amazon.com/s3/)                               | aws.s3                   | [Usage](./aws/s3.md)                 |
| Serverless |                                                                |                          |                                         |
|            | [Lambda](https://aws.amazon.com/lambda/)                       | aws.lambda               | [Usage](./aws/lambda.md)             |
| Other      |                                                                |                          |                                         |
|            | [CloudWatch Logs](https://aws.amazon.com/cloudwatch/)              | aws.cloudwatch.logs      | [Usage](./aws/cloudwatch-logs.md)    |
|            | [CloudWatch Events](https://aws.amazon.com/cloudwatch/)              | aws.cloudwatch.events    | [Usage](./aws/cloudwatch-events.md)  |
|            | [CloudWatch Metrics](https://aws.amazon.com/cloudwatch/)              | aws.cloudwatch.metrics   | [Usage](./aws/cloudwatch-metrics.md) |



#### Microsoft Azure

| Category   | Target                                                                | Kind                  | Configuration                          |
|:-----------|:----------------------------------------------------------------------|:----------------------|:---------------------------------------|
| Stores/db  |                                                                       |                       |                                        |
|            | [Azuresql](https://docs.microsoft.com/en-us/azure/mysql/)             | azure.stores.azuresql | [Usage](./azure/azuresql.md) |
|            | [Mysql](https://aws.amazon.com/dynamodb/)                             | azure.stores.mysql    | [Usage](./azure/mysql.md)    |
|            | [Postgres](https://azure.microsoft.com/en-us/services/postgresql/)    | azure.stores.postgres | [Usage](./azure/postgres.md) |
| Storage    |                                                                       |                       |                                        |
|            | [Blob](https://azure.microsoft.com/en-us/services/storage/blobs/)     | azure.storage.blob    | [Usage](./azure/storage-blob.md)    |
|            | [Files](https://azure.microsoft.com/en-us/services/storage/files/)    | azure.storage.files   | [Usage](./azure/storage-files.md)   |
|            | [Queue](https://docs.microsoft.com/en-us/azure/storage/queues/)       | azure.storage.queue   | [Usage](./azure/storage-queue.md)   |
| EventHubs  |                                                                       |                       |                                        |
|            | [EventHubs](https://azure.microsoft.com/en-us/services/event-hubs/)   | azure.eventhubs       | [Usage](./azure/eventshub.md)       |
| ServiceBus |                                                                       |                       |                                        |
|            | [ServiceBus](https://azure.microsoft.com/en-us/services/service-bus/) | azure.servicebus      | [Usage](./azure/servicebus.md)      |

