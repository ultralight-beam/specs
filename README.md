# Ultralight Beam Specification

> Ultralight Beam describes protocol for sending offline messages that will later be broadcasted through relay nodes.

The protocol itself can be implemented over various transport protocols, it is comparative to a MANET (Mobile Ad-Hoc Network).

## Wire Protocol

The wire protocol defines how messages are packed in order to later be sent through Ultralight Beams.

```
<header-length><command><body-length><body>
```

## Bluetooth
