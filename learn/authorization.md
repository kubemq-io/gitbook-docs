# Authorization

Kubemq's Authorization feature allows to control the access of clients to KubeMQ resources.

## How Permission Work

When a client sends service commands such send data to a channel, subscribe to a channel, pull messages from a queue, Kubemq server checks whether the client has the permission to access the relevant resources and the action.

Access control rule consist from 3 objects:
1. Source - client id




## Authorization Configuration


