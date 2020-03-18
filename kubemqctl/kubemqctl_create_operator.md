## kubemqctl create operator

Create Kubemq Operator

### Synopsis

Create command installs kubemq operator into specific namespace

```
kubemqctl create operator [flags]
```

### Examples

```

	# Install Kubemq operator into "kubemq" namespace
	kubemqctl create operator  

	# Install Kubemq operator into specified namespace
	kubemqctl create operator --namespace my-namespace
 

```

### Options

```
  -h, --help               help for operator
      --namespace string   namespace name (default "kubemq")
```

### Options inherited from parent commands

```
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```
