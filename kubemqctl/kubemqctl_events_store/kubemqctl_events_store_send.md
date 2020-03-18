# Send

Send messages to an 'events store' channel command

## Synopsis

Send command allows to send \(publish\) one or many messages to an 'events store' channel

```text
kubemqctl events_store send [flags]
```

## Examples

```text
    # Send (Publish) message to an 'events store' channel
    kubemqctl events_store send some-channel some-message

    # Send (Publish) message to an 'events store' channel with metadata
    kubemqctl events_store send some-channel some-message --metadata some-metadata

    # Send 10 messages to an 'events store' channel
    kubemqctl events_store send some-channel some-message -m 10

    # Send 100 messages to an 'events store' channel in stream mode
    kubemqctl events_store send some-channel some-message -m 100 -s
```

## Options

```text
  -h, --help              help for send
  -m, --messages int      set how many 'events store' messages to send (default 1)
      --metadata string   set message metadata field
  -s, --stream            set stream of all messages at once
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

