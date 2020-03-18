## kubemqctl create dashboard

Create a Kubemq dashboard command

### Synopsis

Create command allows to deploy a Kubemq Dashboard with configuration options

```
kubemqctl create dashboard [flags]
```

### Examples

```

	# Create default Kubemq Dashboard
	kubemqctl create dashboard
	
	# Create Kubemq dashboard with options - get all flags
	kubemqctl create dashboard --help

```

### Options

```
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

### Options inherited from parent commands

```
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```
