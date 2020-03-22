# Kubemqctl

Kubemqctl is KubeMQ's CLI tool.

## Install Kubemqctl Tool

{% page-ref page="../../kubemqctl/get-started.md" %}

## Install KubeMQ Dashboard

```text
kubemqctl create dashboard
```

## Configuration

The following flags lists the configurable parameters of the KubeMQ cluster create options and their default values.

```text
      --dry-run                        generate dashboard configuration without execute
      --grafana-dashboard-url string   set grafana dashboard url image
      --grafana-image string           set grafana docker image
  -h, --help                           help for dashboard
      --name string                    set kubemq dashboard name (default "kubemq-dashboard")
  -n, --namespace string               set kubemq dashboard namespace (default "kubemq")
  -p, --port int32                     set kubemq dashboard port
      --prometheus-image string        set prometheus docker image
      --prometheus-port int32          set export prometheus port
```

