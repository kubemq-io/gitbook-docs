# Pub/Sub

The publish-subscribe pattern \(or pub/sub, for short\) is a messaging pattern where senders of messages \(publishers\), do not program the messages to be sent directly to specific receivers \(subscribers\). Instead, the programmer “publishes” messages \(events\), without any knowledge of any subscribers there may be.

Similarly, subscribers express interest in one or more events and only receive messages that are of interest, without any knowledge of any publishers.

## Core Features

KubeMQ supports Publish-Subscribe messages patterns with the following core features:

* **Events** - An asynchronous real-time Pub/Sub pattern.
* **Events Store** - An asynchronous Pub/Sub pattern with persistence.
* **Grouping** - Load balancing of events between subscribers
* **Partitioning** - Channels/Topics based wildcards

## Events

Events are an asynchronous real-time Pub/Sub pattern. In Events, multiple senders can send real-time messages to various receivers; however, only if they are currently connected to KubeMQ; there is no message persistence available in this pattern.

![](../.gitbook/assets/event.png)

**Use Cases**

‘Events’ pattern is suitable for cases such as publishing streaming data, logs, notifications, etc.

### Demo - Basic

{% embed url="https://vimeo.com/372195988" %}



### Demo - Group \(Load Balancing\)

{% embed url="https://vimeo.com/372195963" %}



### Demo - Wildcards

{% embed url="https://vimeo.com/372196013" %}



## Events Store

Events Store is an asynchronous Pub/Sub pattern with persistence. In Events Store, multiple senders can send messages to various receivers even if they are not currently. Any receiver can connect to KubeMQ and replay one, any, or all of the messages stored for a specific channel.

![](../.gitbook/assets/event-store.png)

### Events Store Replay Messages Types

KubeMQ supports six types of Events Store subscriptions and replay:

| Type | Description |
| :--- | :--- |
| New Events | KubeMQ will send only new events |
| First Event | KubeMQ will replay all events from the first stored events, as well as send new events |
| Last Event | KubeMQ will replay the last event and continue to send new events |
| From Sequence | KubeMQ will replay events from a specific sequence and continue to send new events |
| From Time | KubeMQ will replay events from a specific time in the past and continue to send new events |
| From Time Delta | KubeMQ will replay events from the particular time delta back \(i.e., 5 min back\) and continue to send new events |

#### Start From New Events

![](../.gitbook/assets/event-store-from-new.png)

{% embed url="https://vimeo.com/372195866" %}



#### Start From First Event

![](../.gitbook/assets/event-store-from-first.png)

{% embed url="https://vimeo.com/372196147" %}



#### Start From Last Event

![](../.gitbook/assets/event-store-from-last.png)

{% embed url="https://vimeo.com/372196161" %}



#### Start From Sequence

![](../.gitbook/assets/event-store-from-seq.png)

{% embed url="https://vimeo.com/372195881" %}



#### Start From Time

![](../.gitbook/assets/event-store-from-time.png)

{% embed url="https://vimeo.com/372195889" %}



#### Start From Time Delta

![](../.gitbook/assets/event-store-from-time-delta.png)

{% embed url="https://vimeo.com/372195899" %}



### Grouping - Load Balancing

KubeMQ supports grouping \(load balancing\) of multiple receivers to share the load

#### Demo

**Example 1**

![](https://github.com/kubemq-io/gitbook-docs/tree/350be2e95d91efd8d8c2e882bbe7d0f0278630f5/learn/demo/kubemqctl-pub-sub-events-store-groups-1.gif)

**Example 2**

![](https://github.com/kubemq-io/gitbook-docs/tree/350be2e95d91efd8d8c2e882bbe7d0f0278630f5/learn/demo/kubemqctl-pub-sub-events-store-groups-2.gif)

**Example 3**

![](https://github.com/kubemq-io/gitbook-docs/tree/350be2e95d91efd8d8c2e882bbe7d0f0278630f5/learn/demo/kubemqctl-pub-sub-events-store-groups-3.gif)

### Unique Client ID

The uniqueness of a client ID is essential when using Events Store. At any given time, only one receiver can connect with a unique Client ID. If two receivers try to connect to KubeMQ with the same Client ID, one of them will be rejected.

**Client ID and Subscription Types Relations**

For each unique Client ID, KubeMQ saves the subscription type in which the client connected; messages can only be replayed once per Client ID and Subscription type.

For example, Receiver with Client ID `client-foo-1` subscribes to a channel `foo.bar` in `First Event` mode. They will get all the messages stored in KubeMQ for `foo.bar` channel from the first message, and then continue to get new events as they come. If this receiver will disconnect from KubeMQ and re-connect again with any subscription type, only new events in `foo.bar` will be delivered for this specific receiver with Client ID `client-foo-1`.

If a Receiver wishes to receive messages on `foo.bar` again, they should subscribe again with a different Client ID than `client-foo-1` such `client-foo-1-retry`.

**Use Cases**

Events Store pattern is suitable for cases in which events are necessary, such as worker’s pool, chats, and inbox related applications.

