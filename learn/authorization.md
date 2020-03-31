---
description: >-
  Kubemq's Authorization feature allows to control the access of clients to
  KubeMQ resources.
---

# Authorization

## How Permission Work

When a client wants to perform an operation such send data to a channel, subscribe to a channel, pull messages from a queue etc, Kubemq server checks whether the client has the permission to access the relevant resources and the action. The client must have been granted the appropriate permission rule in order to complete the operation.

Access control permission rule consist from 4 objects: 

1. Source - the client\_id of each message or request
2. Resource Type - Events, EventsStore, Queues, Commands, Queries
3. Resource Name - Channel
4. Action - Read, Write 



## Authorization Configuration

### Access Control Permission Record

An access control permission record consists from 8 fields:

| Field | Type | Description |
| :--- | :--- | :--- |
| ClientID | string | Client ID - regular expression |
| Events | bool | Allow access to events, true/false  |
| EventsStore | bool | Allow access to events\_store, true/false |
| Queues | bool | Allow access to queues, true/false |
| Commands | bool | Allow access to commands, true/false |
| Queries | bool | Allow access to queries, true/false |
| Channel | string | Channel name - regular expression |
| Read | bool | Allow reading from a resource \(i.e subscribe to a channel\), true/false |
| Write | bool | Allow writing to a resource \(i.e. send message to a channel\), true/false |

The regular expressions for ClientID and Channel allows great flexibility for access control permissions. Let's see some examples.

For ClientID :

| ClientID Regular Expression | Will Grant Access To |
| :--- | :--- |
| client-redis | clients with client\_id = 'client-redis' |
| client\* | any client\_id start with 'client' |
| .\* | any client\_id |

For Channel:

| Channel Regular Expression | Will Grant Access To |
| :--- | :--- |
| foo.bar | Channel = 'foo.bar' |
| foo.bar\* | Any channel starts with foo.bar |
| .\* | Any channel |

### Access Control Permission Rules Set

An array of access control permission records form an access control permission rules set. Every operation will check against all the records in the rules set. In order to grant an access at least one rule must meet the permission requirements.

### Examples

#### Grant access only to client-a to Events resource , both read and write to any channel

```javascript
[
   {
      "ClientID":"client-a",
      "Events":true,
      "EventsStore": false,
      "Queues": false,
      "Commands": false,
      "Queries": flase,
      "Channel":".*",
      "Read":true,
      "Write":true
   }
]
```

#### Grant access to all client ids  starts with sub. to all resources only for reading from foo.bar channel

```javascript
[
   {
      "ClientID":"sub.*",
      "Events":true,
      "EventsStore": true,
      "Queues": true,
      "Commands": true,
      "Queries": true,
      "Channel":"foo.bar",
      "Read":true,
      "Write": false
   }
]
```

Grant access for client-1 to send events only to foo.bar.1 and client-2 to send only to foo.bar.2 

```javascript
[
   {
      "ClientID":"client-1",
      "Events":true,
      "EventsStore": false,
      "Queues": false,
      "Commands": false,
      "Queries": false,
      "Channel":"foo.bar.1",
      "Read":false,
      "Write": true
   },
   {
      "ClientID":"client-2",
      "Events":true,
      "EventsStore": false,
      "Queues": false,
      "Commands": false,
      "Queries": false,
      "Channel":"foo.bar.2",
      "Read":false,
      "Write": true
   },
   
]
```

## Loading Configuration

Kubemq supports two configuration loading options:

1. Set json array on cluster create configuration
2. Set Url of a web service to call and get Authorization configuration json array with automatic reloading options every predefined seconds

{% page-ref page="../configuration/how-to/set-authorization.md" %}



