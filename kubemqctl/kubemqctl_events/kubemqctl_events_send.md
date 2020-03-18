# Send

Send messages to an 'events' channel command

## Synopsis

Send command allows to send \(publish\) one or many messages to an 'events' channel

```text
kubemqctl events send [flags]
```

## Examples

```text
    # Send (Publish) message to a 'events' channel
    kubemqctl events send some-channel some-message

    # Send (Publish) message to a 'events' channel with metadata
    kubemqctl events send some-channel some-message --metadata some-metadata

    # Send (Publish) batch of 10 messages to a 'events' channel
    kubemqctl events send some-channel some-message -m 10

    # Send (Publish) batch of 100 messages to a 'events' channel in stream mode
    kubemqctl events send some-channel some-message -m 100 -s
```

## Options

```text
  -h, --help              help for send
  -m, --messages int      set how many 'events' messages to send (default 1)
      --metadata string   set message metadata field
  -s, --stream            set stream of all messages at once
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

