# Get Dashboard Status

## Using Kubectl

```bash
kubectl get kubemqdashboard -n kubemq
```

Will show:

```bash
NAME               STATUS    ADDRESS                                         PROMETHEUS-VERSION       GRAFANA-VERSION
kubemq-dashboard   Running   http://localhost:32000 http://localhost:31339   prom/prometheus:latest   grafana/grafana:latest
```

