# Notifications

## General

KubeMQ's Notification features allows to subscribe to predefined events channel and receive real-time events for any access to KubeMQ resources.

This feature is useful for external auditing of access control attempts.

## How Notifications Works

KubeMQ administrator can configure an Event channel which will be able to subscribe and receive access log notifications.

Access Notification Record consist from the following fields:

| Field | Type | Description |
| :--- | :--- | :--- |
| Id | string | A unique notification id for the event |
| RefMessageID | string | The message id which triggered the access attempt |
| ClientID | string | The client id which tried to access the resource |
| Resource | string | The resource type: Events, Events Store, Queues, Commands, and Queries |
| Channel | string | The requested channel |
| Action | string | The Action type: Send, Receive, Stream, Ack |
| SubAction | string | The sub action type: Connect |
| Result | string | The result of the request |
| Timestamp | int64 | Unix time of access attempt |
| ResultTimestamp | int64 | Unix time of access result |

## Notification Destinations

A Notification event will be sent to an Event channel with the format of `Report-Channel-Prefix.Resource.Channel`.

For Example:

With `Report-Channel-Prefix` configuration of `notification`

| Resource | Channel | Destination |
| :--- | :--- | :--- |
| Events | foo.bar | notification.events.foo.bar |
| Events Store | foo.bar.2 | notification.events\_store.foo.bar.2 |
| Queues | foo.bar.baz | notification.queues.foo.bar.baz |
| Commands | foo.snork | notification.commands.foo.snork |
| Queries | foo.fum | notification.queires.fum |

## Notification Subscription

Since Events message pattern support wildcards subscriptions, we have great flexibility to which channel we would like to monitor.

For Example:

| Subscribe | Monitor |
| :--- | :--- |
| notification.&gt; | All notification channels |
| notification.events.&gt; | All notification events channels |
| notification.\*.foo.&gt; | All notification in any message pattern with channel name start with foo |
| notification.\*.foo.bar&gt; | All notification in any message pattern with channel name foo.bar only |

## Configuration

KubeMQ allows to configure two settings: 

1. Report Channel Prefix - allows to set the prefix report channel name 

2. Log - Allows to log the notification to console stdout

{% page-ref page="../../configuration/cluster/set-notification.md" %}

{% hint style="success" %}
The Notification feature is available only on KubeMQ Enterprise Edition.

Register for free 30 days license [here](https://account.kubemq.io/login/register).
{% endhint %}

