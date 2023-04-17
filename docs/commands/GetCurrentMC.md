# GetCurrentMC

Command to request/receive current values from device channels.

This command can be sent periodically if [device report data parameter](../parameter-types.md#reporting-data-type) set to
[current](../parameter-types.md#data-type) i.e. = `2`.


## Request

### Format

| Size | Type | Field               |
| ---- | ---- | ------------------- |
| `1`  | byte | command id = `0x18` |
| `1`  | byte | command size = `0`  |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

As a response to this request there is a message with two uplink commands: [GetCurrentMC](./GetCurrentMC.md#response) and [ExAbsCurrentMC](./ExAbsCurrentMC.mc).

### Parameters

The command has no parameters.

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `24`  | `0x18` |
| command size | `0`   | `0x00` |

Message hex dump with LRC: `18 00 4d`


## Response

### Format

| Size | Type | Field                                                                                    |
| ---- | ---- | ---------------------------------------------------------------------------------------- |
| `1`  | byte | command id = `0x18`                                                                      |
| `1`  | byte | command size (dynamic, `2+`)                                                             |
| `1+` | byte | [channels bit set](#channels-bit-set) ([extended bit value](../types.md#extended-value)) |
| `1+` | byte | [channel values](#channel-values) ([extended bit value](../types.md#extended-value))     |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **channels bit set**

[Extended value](../types.md#extended-value) that stores bit set of all channels in command.
Each bit represents one channel.
If bits `0`, `1`, `2`, `3` are set - this means that values from that channels in that order exists in command.
The data for channel at `0` position comes first, then the second, the third and so on.
To store up to `7` channels `1` byte is required. To store up to `14` - `2` bytes and so on.

#### **channel values**

Sequence of [extended values](../types.md#extended-value) to store channel values.
Each value is `32-bit` unsigned integer.

### Examples

#### 4 first channels:

| Field            | Value | Bits                                                                    | Hex      |
| ---------------- | ----- | ----------------------------------------------------------------------- | -------- |
| command id       | `24`  |                                                                         | `0x18`   |
| command size     | `6`   |                                                                         | `0x06`   |
| channels         |       | `0b00001111`                                                            | `0x0f`   |
| channel #0 value | `131` | `0b0000000010000011` <br> with extended bits: <br> `0b0000000110000011` | `0x8301` |
| channel #1 value | `8`   |                                                                         | `08`     |
| channel #2 value | `10`  |                                                                         | `0a`     |
| channel #3 value | `12`  |                                                                         | `0c`     |

Message hex dump with LRC: `18 06 0f 83 01 08 0a 0c c8`

#### single channel #2:

| Field            | Value | Bits         | Hex    |
| ---------------- | ----- | ------------ | ------ |
| command id       | `12`  |              | `0x18` |
| command size     | `2`   |              | `0x02` |
| channels         |       | `0b00000100` | `0x04` |
| channel #1 value | `50`  |              | `0x32` |

Message hex dump with LRC: `18 02 04 32 79`

#### channels #5, #6, #12:

| Field             | Value  | Bits                                                                    | Hex      |
| ----------------- | ------ | ----------------------------------------------------------------------- | -------- |
| command id        | `12`   |                                                                         | `0x18`   |
| command size      | `2`    |                                                                         | `0x07`   |
| channels          |        | `0b0001000001100000` <br> with extended bits: <br> `0b0010000011100000` | `0xe020` |
| channel #5 value  | `8146` | `0b0001111111010010` <br> with extended bits: <br> `0b0011111111010010` | `0xd23f` |
| channel #6 value  | `164`  | `0b0000000010100100` <br> with extended bits: <br> `0b0000000110100100` | `0xa401` |
| channel #12 value | `75`   |                                                                         | `0x4b`   |

Message hex dump with LRC: `18 07 e0 20 d2 3f a4 01 4b 89`


## See also

* [Device report data parameter](../parameter-types.md#reporting-data-type)
* [Extended bit value](../types.md#extended-value)
