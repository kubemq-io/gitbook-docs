# Cluster Configuration



## Basic

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| replicas | int | Desired amount of pods in the cluster | 3 |
| configData | yaml/toml | Load configuration file |  |

## Volume

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| size | string | Desired size of Persisted Volume Claim | "30Gi" |

## License

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| data | string | Set Licence data key |  |
| token | string | Set License Token |  |

## Image

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| image | string | Set kubemq server image | docker.io/kubemq/kubemq-uni:latest |
| pullPolicy | Always/IfNotPresent/Never | Set image pull policy | Always |

## Api

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| disable | bool | Disable Api interface | false |
| expose | ClusterIP/NodePort/LoadBalancer | Desired service type | ClusterIP \(Default\) |
| nodePort | int | Desired port number in NodePort expose type | 31000 |

## gRPC

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| disable | bool | Disable gRPC interface |  |
| expose | ClusterIP/NodePort/LoadBalancer | Desired service type | ClusterIP \(Default\) |
| nodePort | int | Desired port number in NodePort expose type | 31000 |
| bufferSize | int | set subscribe message / requests buffer size to use on server | 100 |
| bodyLimit | int | Set Max size of payload in bytes | 1,048,576 \(1M bytes\) |

## Rest

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| disable | bool | Disable rest interface |  |
| expose | ClusterIP/NodePort/LoadBalancer | Desired service type | ClusterIP \(Default\) |
| nodePort | int | Desired port number in NodePort expose type | 31000 |
| bufferSize | int | set subscribe message / requests buffer size to use on server | 100 |
| bodyLimit | int | Set Max size of payload in bytes | 1,048,576 \(1M bytes\) |

## TLS

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| cert | string | Set tls certification data |  |
| key | string | Set tls private key data |  |
| ca | string | Set tls certification authority  data |  |

## Authentication

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| key | string | Set JWT public key data |  |
| type | string HS256/HS384/HS512/RS256/RS384/RS512/ES256/ES384/ES512 | Set JWT public key signing method |  |

## Authorization

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| policy | string | Set Authorization policy data |  |
| url | string url | Set Optional authorization server url for policy data |  |
| autoReload | int | Set auto reload policy data from url |  |

## Routing

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| data | string | Set Routing data |  |
| url | string url | Set Optional routing server url for routing data |  |
| autoReload | int | Set auto reload data from url |  |

## Store

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| clean | bool | Set clear persistence data on start-up | false |
| path | string | Set persistence file path | ./store |
| maxChannels | int | Set limit number of persistence channels | 0 |
| maxSubscribers | int | Set limit of subscribers per channel | 0 |
| maxMessages | int | Set limit of messages per channel | 0 |
| maxChannelSize | int | Set limit size of channel in bytes | 0 |
| messagesRetentionMinutes | int | Set message retention time in minutes | 1440 |
| purgeInactiveMinutes | int | Set time in minutes of channel inactivity to delete | 1440 |

## Queue

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| maxReceiveMessagesRequest | int | Set max of sending / receiving batch of queue message | 1024 |
| maxWaitTimeoutSeconds | int | Set max expiration allowed for message | 3600 |
| maxExpirationSeconds | int | Set max expiration allowed for message | 43200 |
| maxDelaySeconds | int | set max delay seconds allowed for message | 43200 |
| maxReQueues | int | Set max retires to receive message before discard | 1024 |
| maxVisibilitySeconds | int | Set max time of hold received message before returning to queue | 43200 |
| defaultVisibilitySeconds | int | Set default time of hold received message before returning to queue | 60 |
| defaultWaitTimeoutSeconds | int | Set default time to wait for a message in a queue | 1 |

## Resource

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| limitsCpu | string | Set Limits CPU | 500m |
| limitsMemory | string | Set Limits Memory | 2Gi |
| requestsCpu | string | Set Requests CPU | 1 |
| requestsMemory | string | Set Requests Memory | 512M |

## Node Selectors

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| keys | key/value strings | Set Key Value for node selector |  |

## Health

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| enabled | bool | Set enable/disable health prob |  |
| initialDelaySeconds | int | Set Initial Delay Seconds |  |
| periodSeconds | int | Set Period Seconds Interval |  |
| timeoutSeconds | int | Set Timeout Seconds |  |
| successThreshold | int | Set Success Threshold |  |
| failureThreshold | int | Set Failure Threshold |  |

## Logs

| Field | Type/Options | Description | Example |
| :--- | :--- | :--- | :--- |
| level | int | Set log level, 1 - debug , 2 - info, 3 - warn, 4 - error, 5 - fatal | 2 |
| file | string | Set log file write path |  |

