# Events Hub

Kubemq event-hubs target connector allows services using kubemq server to access event-hubs messaging services.

## Prerequisites

The following are required to run the event-hubs target connector:

* kubemq cluster
* Azure active with event-hubs enable&#x20;
* kubemq-targets deployment

## Configuration

event-hubs target connector configuration properties:

| Properties Key            | Required | Description                       | Example                |
| ------------------------- | -------- | --------------------------------- | ---------------------- |
| end\_point                | yes      | event hubs target endpoint        | "sb://my\_account.net" |
| shared\_access\_key\_name | yes      | event hubs access key name        | "keyname"              |
| shared\_access\_key       | yes      | event hubs shared access key name | "213ase123"            |
| entity\_path              | yes      | event hubs path entity to send    | "mypath"               |

Example:

```yaml
bindings:
  - name: kubemq-query-azure-event-hubs
    source:
      kind: kubemq.query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-azure-eventhubs-connector"
        auth_token: ""
        channel: "azure.eventhubs"
        group:   ""
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: azure.eventhubs
      name: target-azure-eventhubs
      properties:
        end_point: "sb://my_account.net"
        shared_access_key_name: "keyname"
        shared_access_key: "213ase123"
        entity_path: "mypath"
```

## Usage

### send

send metadata setting:

| Metadata Key   | Required | Description                                 | Possible values                                    |
| -------------- | -------- | ------------------------------------------- | -------------------------------------------------- |
| method         | yes      | type of method                              | "send"                                             |
| properties     | no       | event properties key value string interface | "{\\"tag-1\\":\\"test\\",\\"tag-2\\":\\"test2\\"}" |
| data           | yes      | file data (byte array)                      | "bXktZmlsZS1kYXRh"                                 |
| partition\_key | no       | partition key to assign the messages        | "0"                                                |

Example:

```javascript
{
  "metadata": {
    "method": "send",
    "properties": "{\"tag-1\":\"test\",\"tag-2\":\"test2\"}"
  },
  "data": "bXktZmlsZS1kYXRh"
}
```

### send batch

send batch metadata setting:

| Metadata Key   | Required | Description                                     | Possible values                               |
| -------------- | -------- | ----------------------------------------------- | --------------------------------------------- |
| method         | yes      | type of method                                  | "send\_batch"                                 |
| properties     | no       | event properties key value string interface     | "myfile.txt"                                  |
| data           | yes      | file data (byte array)slice  , for each message | "WyJ0ZXN0MSIsInRlc3QyIiwidGVzdDMiLCJ0ZXN0NCJd |
| partition\_key | no       | partition key to assign all the messages        | "0"                                           |

Example:

````javascript
{
  "metadata": {
    "method": "send_batch",
        "properties": "{\"tag-1\":\"test\",\"tag-2\":\"test2\"}"
  },
  "data": "WyJ0ZXN0MSIsInRlc3QyIiwidGVzdDMiLCJ0ZXN0NCJd"
}
```
````
