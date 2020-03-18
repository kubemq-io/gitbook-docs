# Receive

Receive a message from 'events' channel command

## Synopsis

Receive \(Subscribe\) command allows to consume one or many messages from 'events' channel

```text
kubemqctl events receive [flags]
```

## Examples

```text
    # Receive messages from an 'events' channel (blocks until next message)
    kubemqctl events receive some-channel

    # Receive messages from an 'events' channel with group (blocks until next message)
    kubemqctl events receive some-channel -g G1
```

## Options

```text
  -g, --group string   set 'events' channel consumer group (load balancing)
  -h, --help           help for receive
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

