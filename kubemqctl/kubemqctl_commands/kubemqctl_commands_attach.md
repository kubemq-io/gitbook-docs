# Attach

Attach to 'commands' channels command

## Synopsis

Attach command allows to display 'commands' channel content for debugging proposes

```text
kubemqctl commands attach [flags]
```

## Examples

```text
    # attach to all commands channels and output running messages
    kubemqctl commands attach *

    # attach to some-commands 'commands' channel and output running messages
    kubemqctl commands attach some-commands

    # attach to some-commands1 and some-commands2 'commands' channels and output running messages
    kubemqctl commands attach some-commands1 some-commands2 

    # attach to some-commands 'commands' channel and output running messages filter by include regex (some*)
    kubemqctl commands attach some-commands -i some*

    # attach to some-commands 'commands' channel and output running messages filter by exclude regex (not-some*)
    kubemqctl commands attach some-commands -e not-some*
```

## Options

```text
  -e, --exclude stringArray   Set (regex) strings to exclude
  -h, --help                  help for attach
  -i, --include stringArray   Set (regex) strings to include
```

## Options inherited from parent commands

```text
      --config string   set kubemqctl configuration file (default "./.kubemqctl.yaml")
```

