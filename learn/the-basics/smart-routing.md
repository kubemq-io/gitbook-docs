# Smart Routing

## General

KubeMQ smart routing is In-flight and routing tables messaging feature which allows to multicast a messages to many destinations in single operation.

## Multicast Destinations

RPC and Queues **senders** can multicast a message to many channels at once, even to a different messaging pattern. Separate each destination with a `;` and specify the message pattern type with `:`.

### Message Pattern Format

| Pattern | Format | Example |
| :--- | :--- | :--- |
| Events | events: | events: events.foo.bar;events: events.foo.bar.1 |
| Events Store | events\_store: | events\_store: store.foo.bar;events\_store: store.foo.bar.1 |
| Queues | queues: | queues: q1.foo.bar; queues: q2.foo.bar |

### Predefined Routes - Smart routes

A predefined routes rule can be set with KubeMQ Smart Routing configuration and can be used like that:

| Pattern | Format | Will routes |
| :--- | :--- | :--- |
| Routes | routes: all-foo-bar | to all destinations defined by all-foo-bar route |



### Mixing Message Pattern destinations

Mixing message pattern destination is allowed. for example, an events sender can send a message to events\_store subscriber and to a queues subscriber at the same time.

### Examples

| Sends From | Channel Destinations | Will routes to |
| :--- | :--- | :--- |
| Events | foo.bar;foo.bar.1;events\_store: store.foo;queues: q1 | events-&gt;foo.bar, events-&gt;foo.bar.1, events\_store-&gt;store.foo, queues-&gt;q1 |
| Events Store | foo.bar.store;events: bar.1;queues:q2; routes:my-route | events\_store-&gt;foo.bar.store, events-&gt; bar.1, queues -&gt; q2, all destinations defined by my-route |
| Queues | q1.foo.bar;events: bar.1;events\_store:store.foo.1 | queues-&gt; q1.foo.bar, events-&gt; bar.1, events\_store-&gt; store.foo.1 |

## Smart Route Preload Configuration

A routing rule is defined by a record with two fields:

| Field | Type | Description |
| :--- | :--- | :--- |
| Key | string | unique key name for the routing rule |
| Routes | string | channel destinations separated by ; |

{% hint style="danger" %}
Routes cannot point to another Routes Key
{% endhint %}

Example:

Two routing rules:

```javascript
[
   {
      "Key":"all-to-foo-bar",
      "Routes":"events:foo.bar;events_store:foo.bar;queues:foo.bar"
   },
   {
      "Key":"sink-to-events-channel",
      "Routes":"events:sink"
   }
]
```

{% hint style="success" %}
The Smart Route preload configuration feature is available only on KubeMQ Enterprise Edition.

Register for free 30 days license [here](https://account.kubemq.io/login/register).
{% endhint %}
