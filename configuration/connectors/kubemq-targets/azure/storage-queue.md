# Queue

Kubemq queue target connector allows services using kubemq server to access queue messaging services.

## Prerequisites

The following are required to run the queue target connector:

* kubemq cluster
* Azure active storage account
* Azure active with storage enable - with access account
* kubemq-targets deployment

## Configuration

queue target connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| storage\_account | yes | azure storage account name | "my\_account" |
| storage\_access\_key | yes | azure storage access key | "abcd1234" |
| policy | no | exponential or linear | "retry\_policy\_exponential",default\(retry\_policy\_exponential\) |
| max\_tries | no | request max tries \(1 disable\) | "1",default\(1\) |
| try\_timeout | no | Maximum time allowed for any single try | "3000",default\(10000\) milliseconds |
| retry\_delay | no | Backoff amount for each retry | "1000",default\(600\)   milliseconds |
| max\_retry\_delay | no | delay between retries | "1000",default\(1800\)  milliseconds |

Example:

```yaml
bindings:
  - name: kubemq-query-azure-queue
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-azure-queue-connector"
        auth_token: ""
        channel: "azure.storage.queue"
        group:   ""
        concurrency: "1"
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: azure.storage.queue
      name: azure-storage-queue
      properties:
        storage_account: "id"
        storage_access_key: "key".
        max_retry_delay: "180000"
        max_tries: "1"
        policy: retry_policy_exponential
        retry_delay: "60000"
        try_timeout: "1000"
```

## Usage

### Create

Create metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "create" |
| service\_url | yes | service url path | "[https://test.queue.core.windows.net/test/test.txt](https://test.queue.core.windows.net/test/test.txt)" |
| queue\_name | yes | the name of the queue to create | "my\_queue" |
| queue\_metadata | no | key value string string queue Metadata | "{"tag":"test","name":"myname"}",default\(none\) |

```javascript
{
  "metadata": {
    "method": "create",
    "queue_name": "my_queue",
    "service_url": "https://test.end.point.test.net"
  },
  "data": null
}
```

### Push

Push metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "push" |
| service\_url | yes | service url path | "[https://test.queue.core.windows.net/test/test.txt](https://test.queue.core.windows.net/test/test.txt)" |
| queue\_name | yes | the name of the queue to send the message to | "my\_queue" |
| queue\_metadata | no | key value string string queue Metadata | "{"tag":"test","name":"myname"}",default\(none\) |
| visibility\_timeout | no | visibility timeout value,in milliseconds | "2000000000",default\(100000000\) |
| time\_to\_live | no | maximum time to allow the message to be in the queue,in milliseconds | "2000000000",default\(100000000\) |

Example:

```javascript
{
  "metadata": {
    "method": "push",
    "queue_name": "test",
    "service_url": "https://test.end.point.test.net"
  },
  "data": "bXktZmlsZS1kYXRh"
}
```

### Get Message Count

Get Message Count metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "get\_messages\_count" |
| service\_url | yes | service url path and | "[https://test.queue.core.windows.net/test](https://test.queue.core.windows.net/test)" |
| queue\_name | yes | the name of the queue | "my\_queue" |

Example:

```javascript
{
  "metadata": {
    "method": "get_messages_count",
    "queue_name": "test",
    "service_url": "https://test.end.point.test.net"
  },
  "data": null
}
```

### Delete

Delete metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "delete" |
| service\_url | yes | service url path and | "[https://test.queue.core.windows.net/test](https://test.queue.core.windows.net/test)" |
| queue\_name | yes | the name of the queue | "my\_queue" |

Example:

```javascript
{
  "metadata": {
    "method": "delete",
    "queue_name": "test",
    "service_url": "https://test.end.point.test.net"
  },
  "data": null
}
```

### Peek

Peek metadata setting:

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "peek" |
| file\_name | yes | the name of the file to delete | "myfile.txt" |
| service\_url | yes | service url path and | "[https://test.queue.core.windows.net/test/test.txt](https://test.queue.core.windows.net/test/test.txt)" |
| max\_messages | no | max number of messages to receive int32 | "10",default\(32\) |

Example:

```javascript
{
  "metadata": {
    "method": "peek",
    "queue_name": "test",
    "service_url": "https://test.end.point.test.net"
  },
  "data": null
}
```

### Pop

Pop metadata setting:

Pop will remove the message

| Metadata Key | Required | Description | Possible values |
| :--- | :--- | :--- | :--- |
| method | yes | type of method | "pop" |
| file\_name | yes | the name of the file to delete | "myfile.txt" |
| service\_url | yes | service url path and | "[https://test.queue.core.windows.net/test/test.txt](https://test.queue.core.windows.net/test/test.txt)" |
| max\_messages | no | max number of messages to receive int32 | "10",default\(32\) |

Example:

```javascript
{
  "metadata": {
    "method": "pop",
    "queue_name": "test",
    "service_url": "https://test.end.point.test.net"
  },
  "data": null
}
```

