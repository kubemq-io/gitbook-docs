# Service Bus

Kubemq servicebus target connector allows services using kubemq server to access servicebus messaging services.

## Prerequisites

The following are required to run the servicebus target connector:

* kubemq cluster
* Azure active with servicebus enable&#x20;
* kubemq-targets deployment

## Configuration

servicebus target connector configuration properties:

| Properties Key            | Required | Description                       | Example                |
| ------------------------- | -------- | --------------------------------- | ---------------------- |
| end\_point                | yes      | event hubs target endpoint        | "sb://my\_account.net" |
| shared\_access\_key\_name | yes      | event hubs access key name        | "keyname"              |
| shared\_access\_key       | yes      | event hubs shared access key name | "213ase123"            |

Example:

```yaml
bindings:
  - name: kubemq-query-azure-servicebus
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-azure-servicebus-connector"
        auth_token: ""
        channel: "azure.servicebus"
        group:   ""
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: azure.servicebus
      name: target-azure-servicebus
      properties:
        end_point: "sb://my_account.net"
        shared_access_key_name: "keyname"
        shared_access_key: "213ase123"
        queue_name: "mypath"
```

## Usage

### send

send metadata setting:

| Metadata Key   | Required | Description          | Possible values                 |
| -------------- | -------- | -------------------- | ------------------------------- |
| method         | yes      | type of method       | "send"                          |
| label          | no       | the message label    | "my\_label"                     |
| content\_type  | no       | message content type | "content\_type"                 |
| time\_to\_live | no       | message time to live | "1000000000"default(1000000000) |

Example:

```javascript
{
  "metadata": {
    "method": "send",
    "label": "my_label"
  },
  "data": "bXktZmlsZS1kYXRh"
}
```

### send batch

send batch metadata setting:

| Metadata Key   | Required | Description          | Possible values                 |
| -------------- | -------- | -------------------- | ------------------------------- |
| method         | yes      | type of method       | "send\_batch"                   |
| label          | no       | the message label    | "my\_label"                     |
| content\_type  | no       | message content type | "content\_type"                 |
| time\_to\_live | no       | message time to live | "1000000000"default(1000000000) |

Example:

````javascript
{
  "metadata": {
    "method": "send_batch",
        "label": "my_label"
  },
  "data": "WyJ0ZXN0MSIsInRlc3QyIiwidGVzdDMiLCJ0ZXN0NCJd"
}
```
````
