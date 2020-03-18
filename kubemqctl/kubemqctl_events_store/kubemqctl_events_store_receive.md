# Receive

Receive a messages from an 'events store'

## Synopsis

Receive \(Subscribe\) command allows to consume messages from an 'events store' with options to set offset parameters

```text
kubemqctl events_store receive [flags]
```

## Examples

```text
    # Receive messages from an 'events store' channel (blocks until next message)
    kubemqctl events_store receive some-channel

    # Receive messages from an 'events channel' with group(blocks until next message)
    kubemqctl events_store receive some-channel -g G1
```

## Options

```text
  -g, --group string   set 'events_store' channel consumer group (load balancing)
  -h, --help           help for receive
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

