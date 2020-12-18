# Kinesis

Kubemq kinesis target connector allows services using kubemq server to access aws kinesis service.

## Prerequisites

The following required to run the aws-kinesis target connector:

* kubemq cluster
* aws account with kinesis active service
* kubemq-source deployment

## Configuration

sns target connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| aws\_key | yes | aws key | aws key supplied by aws |
| aws\_secret\_key | yes | aws secret key | aws secret key supplied by aws |
| region | yes | region | aws region |
| token | no | aws token \("default" empty string | aws token |

Example:

```yaml
bindings:
  - name: kubemq-query-aws-kinesis
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-aws-kinesis"
        auth_token: ""
        channel: "query.aws.kinesis"
        group:   ""
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: aws.kinesis
      name: aws-kinesis
      properties:
        aws_key: "id"
        aws_secret_key: 'json'
        region:  "region"
        token: ""
```

## Usage

### List Streams

list kinesis streams

List Streams:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "list\_streams" |

Example:

```javascript
{
  "metadata": {
    "method": "list_streams"
  },
  "data": null
}
```

### List Stream Consumers

list kinesis Stream Consumers.

List Stream Consumers:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "list\_stream\_consumers" |
| stream\_arn | yes | aws stream arn of the desired stream | "arn::mystream" |

Example:

```javascript
{
  "metadata": {
    "method": "list_stream_consumers",
    "stream_arn": "arn::mystream"
  },
  "data": null
}
```

### Create Stream

Create a kinesis Stream.

Create Stream:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "create\_stream" |
| stream\_name | yes | aws stream name as string | "string" |
| shard\_count | no | number of shards to create \(default 1\) | "1" |

Example:

```javascript
{
  "metadata": {
    "method": "create_stream",
    "stream_name": "my_stream",
    "shard_count": "1"
  },
  "data": null
}
```

### List Shards

list stream Shards .

List Shards:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "list\_shards" |
| stream\_name | yes | aws stream name as string | "string" |

Example:

```javascript
{
  "metadata": {
    "method": "list_shards",
    "stream_name": "my_stream"
  },
  "data": null
}
```

### Get Shard Iterator

Get Shard Iterator used to preform get data .

Get Shard Iterator:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "get\_shard\_iterator" |
| stream\_name | yes | aws stream name as string | "string" |
| shard\_iterator\_type | yes | aws shard iterator type | see [https://docs.aws.amazon.com/kinesis/latest/APIReference/API\_GetShardIterator.html](https://docs.aws.amazon.com/kinesis/latest/APIReference/API_GetShardIterator.html) |
| shard\_id | yes | aws shard full id \(can be acquired using list shard\) | see [https://docs.aws.amazon.com/kinesis/latest/APIReference/API\_GetShardIterator.html](https://docs.aws.amazon.com/kinesis/latest/APIReference/API_GetShardIterator.html) |

Example:

```javascript
{
  "metadata": {
    "method": "get_shard_iterator",
    "shard_iterator_type": "LATEST",
    "stream_name": "my_stream",
    "shard_id": "8619-AWE1"
  },
  "data": null
}
```

### Put Record

Send data to stream .

Put Record:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "put\_record" |
| stream\_name | yes | aws stream name as string | "string" |
| partition\_key | yes | determines which shard in the stream the data record is assigned to. | see [https://docs.aws.amazon.com/kinesis/latest/APIReference/API\_PutRecord.html](https://docs.aws.amazon.com/kinesis/latest/APIReference/API_PutRecord.html) |
| data | yes | Message to send to stream | string |

Example:

```javascript
{
  "metadata": {
    "method": "put_record",
    "partition_key": "0356",
    "stream_name": "my_stream"
  },
  "data": "eyJteV9yZXN1bHQiOiJvayJ9"
}
```

### Put Records

Send multi data to a stream .

Put Records:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "put\_records" |
| stream\_name | yes | aws stream name as string | "string" |
| data | yes | Key value pair of partition\_key\(string\) and message\(\[\]byte\) | key value of partition\_key and message as key value pair [https://docs.aws.amazon.com/kinesis/latest/APIReference/API\_PutRecord.html](https://docs.aws.amazon.com/kinesis/latest/APIReference/API_PutRecord.html) |

Example:

```javascript
{
  "metadata": {
    "method": "put_records",
    "stream_name": "my_stream"
  },
  "data": "eyIxIjoiZXlKdGVWOXlaWE4xYkhRaU9pSnZheUo5IiwiMiI6ImV5SnRlVjl5WlhOMWJIUXlJam9pYjJzaEluMD0ifQ=="
}
```

### Put Records

Send multi data to a stream .

Put Records:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "put\_records" |
| stream\_name | yes | aws stream name as string | "string" |
| data | yes | Key value pair of partition\_key\(string\) and message\(\[\]byte\) | key value of partition\_key and message as key value pair [https://docs.aws.amazon.com/kinesis/latest/APIReference/API\_PutRecord.html](https://docs.aws.amazon.com/kinesis/latest/APIReference/API_PutRecord.html) |

Example:

```javascript
{
  "metadata": {
    "method": "put_records",
    "stream_name": "my_stream"
  },
  "data": "eyIxIjoiZXlKdGVWOXlaWE4xYkhRaU9pSnZheUo5IiwiMiI6ImV5SnRlVjl5WlhOMWJIUXlJam9pYjJzaEluMD0ifQ=="
}
```

### Get Records

Get multi data from a stream .

Get Records:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "get\_records" |
| stream\_name | yes | aws stream name as string | "string" |
| limit | no | Number of limit message to get \(default "1"\) | "int value" |

Example:

```javascript
{
  "metadata": {
    "method": "put_records",
    "stream_name": "my_stream",
    "limit": "1"
  },
  "data": null
}
```

