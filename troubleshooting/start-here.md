# Start Here

## Frequently Asked Questions

### 1. My Cluster is not accessible

#### Check cluster status

{% page-ref page="../how-to/get-cluster-status.md" %}

#### Check cluster logs

{% page-ref page="../how-to/get-cluster-logs.md" %}

### 2. Cannot scale my cluster to more than 3 pods

KubeMQ community edition limits the cluster size to 3 pods

### 3. My cluster stop working when i scaled down to one pod

KubeMQ cluster need at least 2 pods to run in order to allow traffic to be processed.

Check out 

{% page-ref page="../learn/cluster-scale.md" %}



