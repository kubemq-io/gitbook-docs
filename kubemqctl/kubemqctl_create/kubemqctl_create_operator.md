# Operator

Create Kubemq Operator

## Synopsis

Create command installs kubemq operator into specific namespace

```text
kubemqctl create operator [flags]
```

## Examples

```text
    # Install Kubemq operator into "kubemq" namespace
    kubemqctl create operator  

    # Install Kubemq operator into specified namespace
    kubemqctl create operator --namespace my-namespace
```

## Options

```text
  -h, --help               help for operator
      --namespace string   namespace name (default "kubemq")
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

