# GetExAbsCurrentMC

Command to request current consumption absolute values from device channels.


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | extra flag = `0x1f` |
| `1`  | `uint8` | command id = `0x0f` |
| `1`  | `uint8` | command size = `0`  |

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

This command can be sent periodically if [device report data parameter](../parameter-types.md#reporting-data-type) set to
[current](../parameter-types.md#data-type) i.e. = `2`.

### Format

| Size   | Type                                               | Field                                                      |
| ------ | -------------------------------------------------- | ---------------------------------------------------------- |
| `1`    | `uint8`                                            | extra flag = `0x1f`                                        |
| `1`    | `uint8`                                            | command id = `0x0f`                                        |
| `1`    | `uint8`                                            | command size (dynamic, `3+`)                               |
| `1..5` | [extended value](../types.md#extended-value)       | [channels bit set](../parameter-types.md#channels-bit-set) |
| `1`    | [pulse coefficient](../types.md#pulse-coefficient) | channel `1` pulse coefficient                              |
| `1..5` | [extended value](../types.md#extended-value)       | channel `1` value                                          |
| `1`    | [pulse coefficient](../types.md#pulse-coefficient) | channel `2` pulse coefficient                              |
| `1..5` | [extended value](../types.md#extended-value)       | channel `2` value                                          |
| ...    | ...                                                | ...                                                        |
| `1`    | [pulse coefficient](../types.md#pulse-coefficient) | channel `N` pulse coefficient                              |
| `1..5` | [extended value](../types.md#extended-value)       | channel `N` value                                          |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### **channels bit set**

[See details](../parameter-types.md#channels-bit-set).

### Examples

#### absolute current values from channel `4`:

| Field                         | Value | Bits                                                                      | Hex      |
| ----------------------------- | ----- | ------------------------------------------------------------------------- | -------- |
| extra flag                    | `31`  |                                                                           | `0x1f`   |
| command id                    | `15`  |                                                                           | `0x0f`   |
| command size                  | `4`   |                                                                           | `0x04`   |
| channels                      | `4`   | `0b00001000`                                                              | `0x08`   |
| channel `4` pulse coefficient | `100` |                                                                           | `0x64`   |
| channel `4` value             | `342` | `0b0000000101010110` <br/> with extended bits: <br/> `0b0000001011010110` | `0xd602` |

Message hex dump with LRC: `1f 0f 04 08 64 d6 02 f9`


## See also

* [Device report data parameter](../parameter-types.md#reporting-data-type)
* [Extended value](../types.md#extended-value)
* [Channels bit set](../parameter-types.md#channels-bit-set)
