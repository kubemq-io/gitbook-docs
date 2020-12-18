# EventHubs

Kubemq azure-eventhubs source connector allows services using kubemq server to access google eventhubs server.

## Prerequisites

The following required to run the azure-eventhubs source connector:

* kubemq cluster
* azure-eventhubs set up
* kubemq-source deployment

## Configuration

event-hubs source connector configuration properties:

| Properties Key | Required | Description | Example |
| :--- | :--- | :--- | :--- |
| end\_point | yes | event hubs target endpoint | "sb://my\_account.net" |
| shared\_access\_key\_name | yes | event hubs access key name | "keyname" |
| shared\_access\_key | yes | event hubs shared access key name | "213ase123" |
| entity\_path | yes | event hubs path entity to subscribe | "mypath" |
| partition\_id | yes | event hubs partition\_id to listen | "0" |
| receive\_type | no | event hubs path entity to send | "latest\_offset","from\_timestamp","with\_consumer\_group","with\_epoch","with\_prefetch\_count","with\_starting\_offset" Default\(with\_starting\_offset\) |
| partition\_id | yes | event hubs partition\_id to listen | "0" |
| time\_stamp | no | timestamp to read events from must supply with from\_timestamp\(RFC3339\) | "0" |
| with\_consumer\_group | no | consumer group to assign the listener must supply with with\_consumer\_group\(RFC3339\) | "0" |
| with\_epoch | no | timestamp to read from w must supply with with\_epoch\(RFC3339\) | "0" |
| with\_prefetch\_count | no | event hubs partition\_id to listen | "0" |
| with\_starting\_offset | no | event hubs partition\_id to listen | "0" |

Example:

```yaml
bindings:
  - name: kubemq-query-azure-eventhubs
    source:
      kind: query
      name: kubemq-query
      properties:
        address: "kubemq-cluster:50000"
        client_id: "kubemq-query-azure-eventhubs-connector"
        auth_token: ""
        channel: "query.azure.eventhubs"
        group:   ""
        auto_reconnect: "true"
        reconnect_interval_seconds: "1"
        max_reconnects: "0"
    target:
      kind: azure.eventhubs
      name: azure-eventhubs
      properties:
          end_point: "sb://my_account.net"
          shared_access_key_name: "keyname"
          shared_access_key: "213ase123"
          entity_path: "mypath"
          partition_id: "0"
```

