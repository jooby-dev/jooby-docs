# HourMCEx

This command is extended version of [HourMCEx](#./HourMC.md). Command could send up to 256 hours.


## Event

### Format

| Size   | Type                                            | Field                                               |
| ------ | ----------------------------------------------- | --------------------------------------------------- |
| `1`    | `byte`                                          | command id = `0x17`                                 |
| `1`    | `byte`                                          | command size (dynamic, `6+`)                        |
| `2`    | [packed date](../../types.md#packed-date)       | [date](#date)                                       |
| `1`    | byte                                            | [hour](#hour)                                       |
| `1`    | byte                                            | [hours](#hours)                                     |
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

#### **hours**

It`s full value of pulse counter with diff for each previous hours

#### **channels bit set**

[See details](../../types.md#channels-bit-set).

### Examples

#### channels `1`, `2`, `3`, `4`:

| Field             | Value                     | Bits                                                                    | Hex      |
| ----------------- | ------------------------- | ----------------------------------------------------------------------- | -------- |
| command id        | `23`                      |                                                                         | `0x17`   |
| command size      | `15`                      |                                                                         | `0x10`   |
| date              | `2023.12.23 00:00:00 GMT` | `0b0010111110010111`                                                    | `0x2f97` |
| hour              | hour: `12:00`             | `0b00001100`                                                            | `0x0c`   |
| hours             | hours: `1`                | `0b00000000`                                                            | `0x00`   |
| channels          | `1`, `2`, `3`, `4`        | `0b00001111` <br> the same with extended bits                           | `0x0f`   |
| channel `1` value | `131`                     | `0b0000000010000011` <br> with extended bits: <br> `0b0000000110000011` | `0x8301` |
| channel `1` diff  | `10`                      |                                                                         | `0x0a`   |
| channel `2` value | `832`                     | `0b0000001101000000` <br> with extended bits: <br> `0b0000011011000000` | `0xc006` |
| channel `2` diff  | `12`                      |                                                                         | `0x0c`   |
| channel `3` value | `38`                      |                                                                         | `0x26`   |
| channel `3` diff  | `8`                       |                                                                         | `0x08`   |
| channel `4` value | `234`                     | `0b0000000011101010` <br> with extended bits: <br> `0b0000000111101010` | `0xea01` |
| channel `4` diff  | `11`                      |                                                                         | `0x0b`   |

Message hex dump with LRC: `17 10 2f 97 0c 00 0f 83 01 0a c0 06 0c 26 08 ea 01 0b 7a`


## See also

* [Packed date](../../types.md#packed-date)
* [Extended value](../../types.md#extended-value)
* [Channels bit set](../../types.md#channels-bit-set)
