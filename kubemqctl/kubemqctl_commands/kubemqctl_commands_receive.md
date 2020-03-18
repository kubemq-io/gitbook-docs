# Receive

Receive a message from 'commands' channel command

## Synopsis

Receive \(Subscribe\) command allows to consume a message from 'commands' channel and response with appropriate reply

```text
kubemqctl commands receive [flags]
```

## Examples

```text
    # Receive commands from a 'commands' channel (blocks until next message)
    kubemqctl commands receive some-channel

    # Receive commands from a 'commands' channel with group (blocks until next message)
    kubemqctl commands receive some-channel -g G1
```

## Options

```text
  -a, --auto-response   set auto response executed command for each command received
  -g, --group string    set 'commands' channel consumer group (load balancing)
  -h, --help            help for receive
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

