# Clustering

Kubemq cluster protocol base on [Raft](https://raft.github.io/) consensus algorithm. 

Since the Kubemq leader node is handling all the incoming and the outgoing data adding more Kubemq nodes will not scale horizontally but will increase the availability of Kubemq cluster. 

### Cluster Size

 For a cluster of `N` nodes in size to remain operational, at least `(N/2)+1` nodes must be up and running, and be in contact with each other.

Clusters of 3, 5, 7, or 9, nodes are most practical. Clusters of those sizes can tolerate failures of 1, 2, 3, and 4 nodes respectively.

Clusters with a greater number of nodes start to become unweildy, due to the number of nodes that must be contacted before a store operation \(such message queue or event\_store message \) can be ack'ed to the sender they can be committed to storage layer.

There is little point running clusters with even numbers of KubeMQ  nodes. For example, let's say we have one cluster of 3 nodes, and a second cluster of 4 nodes. In each case, for the cluster to reach consensus on a given change, a majority of nodes within the cluster are required to have agreed to the change.

Specifically, a majority is defined as `(N/2)+1` where `N` is the number of nodes in the cluster. For a 3-node a majority is 2; for a 4-node cluster a majority is 3. Therefore a 3-node cluster can tolerate the failure of a single node. However a 4-node cluster can also only tolerate a failure of a single node.

So a 4-node cluster is no more fault-tolerant than a 3-node cluster, so running a 4-node cluster provides no advantage over a 3-node cluster. Only a 5-node cluster can tolerate the failure of 2 nodes. An analogous argument applies to 5-node vs. 6-node clusters, and so on.

| Cluster Nodes | Majority Needed | Can Tolerate Failure  |
| :--- | :--- | :--- |
| 3 | 2 | 1 |
| 4 | 3 | 1 |
| 5 | 3 | 2 |
| 6 | 4 | 2 |
| 7 | 4 | 3 |
| 8 | 5 | 3 |
| 9 | 5 | 4 |

### Cluster Persistency

KubeMQ supports two modes of cluster persistency:

* Files on local container ephemeral volume - default
* Files on PVC \(Persisted Volume Claim\)

Consider:

|  | Local Volume | Persisted Volume Claim |
| :--- | :--- | :--- |
| Speed | Fast | Slow |
| Recovery | Only per raft availability | Any failure |

For Persisted Volume Claim configuration, please checkout the link below. 

{% page-ref page="../configuration/configuration/set-persistence-volume.md" %}



