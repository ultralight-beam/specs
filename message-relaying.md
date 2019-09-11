# Message Relaying

> Version: 0.1.0 (Draft)
>
> Authors: Dean Eigenmann <dean@status.im>

## Table of Contents

1. [Abstract](#abstract)
2. [Definitions](#definitions)
3. [Relaying](#relaying)

## Abstract

In this specification, we describe how nodes relay messages. This includes nodes sending initial messages as well as nodes relaying messages they have received from other nodes.

## Definitions

| Term        | Definition                              |
| ----------- | --------------------------------------- |
| Origin      | The initial sender of any message.      |
| Last sender | The last node a message hopped through. |


## Relaying

There are three modes with which a packet can be sent to peers, they both depend on the message along with the nodes state.

A message MUST either contain a `recipient` address or a target `protocol`.

<!-- @TODO REFERENCE MESSAGE SPEC THAT WILL DEFINE RECIPIENT AND PROTOCOL -->

If a message contains a `recipient`, a node MUST initially try and send it to the recipient's address. If a node does not have a direct connection it MAY send it to any number of its peers.

If a message contains a `protocol`, a node MUST initially try and send it to any peer that supports it. If non of the nodes peers support this protocol, we MAY send it to any number of its peers.

When sending a message to any peer, a node MUST ensure they are neither the `origin` nor `last sender`. A node SHOULD abstain from flooding a message given it has a more effective manner to route it towards its target.

## Footnotes
1. <https://github.com/ultralight-beam/UB.swift/pull/42> - A pull request in the swift implementation that implements this sending logic.

<!-- @TODO THINK ABOUT TRANSMITTING SOME FORM OF ROUTE LIST SO WE NEVER SEND IT TO ANY PRIOR RECIPIENT -->

