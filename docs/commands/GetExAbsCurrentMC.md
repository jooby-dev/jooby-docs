# GetExAbsCurrentMC

Command to request/receive current consumption absolute values from device channels.

This command can be sent periodically if [device report data parameter](../parameter-types.md#reporting-data-type) set to
[current](../parameter-types.md#data-type) i.e. = `2`.


## Request

### Format

| Size | Type   | Field               |
| ---- | ------ | ------------------- |
| `1`  | `byte` | extra flag = `0x1f` |
| `1`  | `byte` | command id = `0x0f` |
| `1`  | `byte` | command size = `0`  |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| extra flag   | `31`  | `0x1f` |
| command id   | `15`  | `0x0f` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `1f 0f 00 45`


## Response

### Format

| Size           | Type                                                                   | Field                                                                                             |
| -------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `1`            | `byte`                                                                 | extra flag = `0x1f`                                                                               |
| `1`            | `byte`                                                                 | command id = `0x0f`                                                                               |
| `1`            | `byte`                                                                 | command size (dynamic, `3+`)                                                                      |
| `1..5`         | [extended value](../types.md#extended-value)                           | [channels bit set](#channels-bit-set)                                                             |
| `[1..5]*n + n` | sequence of bytes and [extended values](../../types.md#extended-value) | [channel values sequence with pulse coefficient](#channel-values-sequence-with-pulse-coefficient) |

> `n` - amount of selected channels.

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### **channels bit set**

[See details](../types.md#channels-bit-set).

#### **channel values sequence with pulse coefficient**

It's current consumption absolute values for selected channels.
<br>
[See details](../types.md#channel-values-with-pulse-coefficient).

### Examples

#### absolute current values from channel #3:

| Field                        | Value | Bits                                                                    | Hex      |
| ---------------------------- | ----- | ----------------------------------------------------------------------- | -------- |
| extra flag                   | `31`  |                                                                         | `0x1f`   |
| command id                   | `15`  |                                                                         | `0x0f`   |
| command size                 | `4`   |                                                                         | `0x04`   |
| channels                     | #3    | `0b00001000`                                                            | `0x08`   |
| channel #3 pulse coefficient | `100` |                                                                         | `0x64`   |
| channel #3 value             | `342` | `0b0000000101010110` <br> with extended bits: <br> `0b0000001011010110` | `0xd602` |

Message hex dump with LRC: `1f 0f 04 08 64 d6 02 f9`


## See also

* [Device report data parameter](../parameter-types.md#reporting-data-type)
* [Extended value](../types.md#extended-value)
* [Channels bit set](../types.md#channels-bit-set)
* [Channel values with pulse coefficient](../types.md#channel-values-with-pulse-coefficient)
