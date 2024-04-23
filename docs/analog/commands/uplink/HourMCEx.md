# HourMCEx

This command is an extended version of [HourMC](./HourMC.md). Command could send up to 256 hours if transport support.
To get this uplink need to set param [mqtt data send config](../../parameter-types.md#mqtt-data-send-config)

## Event

### Format

| Size   | Type                                            | Field                                               |
| ------ | ----------------------------------------------- | --------------------------------------------------- |
| `1`    | `uint8`                                         | extra flag = `0x1f`                                 |
| `1`    | `uint8`                                         | command id = `0x31`                                 |
| `1`    | `uint8`                                          | command size (dynamic, `6+`)                        |
| `2`    | [packed date](../../types.md#packed-date)       | [date](#date)                                       |
| `1`    | uint8                                            | [hour](#hour)                                       |
| `1`    | uint8                                            | [hours](#hours)                                     |
| `1..5` | [extended value](../../types.md#extended-value) | [channels bit set](../../types.md#channels-bit-set) |
| `1..5` | [extended value](../../types.md#extended-value) | channel `1` value                                   |
| `1..5` | [extended value](../../types.md#extended-value) | channel `1` diff `1`                                |
| `1..5` | [extended value](../../types.md#extended-value) | channel `1` diff `2`                                |
| `1..5` | [extended value](../../types.md#extended-value) | channel `2` value                                   |
| `1..5` | [extended value](../../types.md#extended-value) | channel `2` diff `1`                                |
| `1..5` | [extended value](../../types.md#extended-value) | channel `2` diff `2`                                |
| ...    | ...                                             | ...                                                 |
| `1..5` | [extended value](../../types.md#extended-value) | channel `N` value                                   |
| `1..5` | [extended value](../../types.md#extended-value) | channel `N` diff `1`                                |
| `1..5` | [extended value](../../types.md#extended-value) | channel `N` diff `2`                                |

It's a command with a [two-bytes header](../../message.md#command-with-a-two-bytes-header).

### Parameters

#### **date**

The command contains pulse counter of channels for this date.
<br>
[See details](../../types.md#packed-date).

#### **hour**

It's a start hour.

#### **hours**

Count the pulse counter's full value with a diff for each previous hour. The hours value 0 means 1 hour.

#### **channels bit set**

[See details](../../types.md#channels-bit-set).

### Examples

#### channels `1`, `2`, `3`, `4`:

| Field             | Value                     | Bits                                                                    | Hex      |
| ----------------- | ------------------------- | ----------------------------------------------------------------------- | -------- |
| extra flag        | `31`                      |                                                                         | `0x1f`   |
| command id        | `49`                      |                                                                         | `0x31`   |
| command size      | `16`                      |                                                                         | `0x10`   |
| date              | `2023.12.23 00:00:00 GMT` | `0b0010111110010111`                                                    | `0x2f97` |
| hour              | hour: `12:00`             | `0b00001100`                                                            | `0x0c`   |
| hours             | hours: `1`                | `0b00000001`                                                            | `0x01`   |
| channels          | `1`, `2`, `3`, `4`        | `0b00001111` <br> the same with extended bits                           | `0x0f`   |
| channel `1` value | `131`                     | `0b0000000010000011` <br> with extended bits: <br> `0b0000000110000011` | `0x8301` |
| channel `1` diff  | `10`                      |                                                                         | `0x0a`   |
| channel `2` value | `832`                     | `0b0000001101000000` <br> with extended bits: <br> `0b0000011011000000` | `0xc006` |
| channel `2` diff  | `12`                      |                                                                         | `0x0c`   |
| channel `3` value | `38`                      |                                                                         | `0x26`   |
| channel `3` diff  | `8`                       |                                                                         | `0x08`   |
| channel `4` value | `234`                     | `0b0000000011101010` <br> with extended bits: <br> `0b0000000111101010` | `0xea01` |
| channel `4` diff  | `11`                      |                                                                         | `0x0b`   |

Message hex dump with LRC: `1f 31 10 2f 97 0c 01 0f 83 01 0a c0 06 0c 26 08 ea 01 0b 5d`


## See also

* [Packed date](../../types.md#packed-date)
* [Extended value](../../types.md#extended-value)
* [Channels bit set](../../types.md#channels-bit-set)
