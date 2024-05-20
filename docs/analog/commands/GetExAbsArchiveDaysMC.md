# GetExAbsArchiveDaysMC

Command to request daily consumption (absolute values) of device channels from the archive.


## Request

### Format

| Size   | Type                                         | Field                                            |
| ------ | -------------------------------------------- | ------------------------------------------------ |
| `1`    | `uint8`                                      | extra flag = `0x1f`                              |
| `1`    | `uint8`                                      | command id = `0x0d`                              |
| `1`    | `uint8`                                      | command size (dynamic, `4+`)                     |
| `2`    | [packed date](../types.md#packed-date)       | [start date](#start-date)                        |
| `1..5` | [extended value](../types.md#extended-value) | [channels bit set](../types.md#channels-bit-set) |
| `1`    | `uint8`                                      | [days](#days)                                    |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### **start date**

Start date for requested day pulse counter's values.
<br/>
[See details](../types.md#packed-date).

#### **channels bit set**

[See details](../types.md#channels-bit-set).

#### **days**

The number of days to get data from archive.

### Examples

#### channels `1`:

| Field        | Value                     | Bits                 | Hex      |
| ------------ | ------------------------- | -------------------- | -------- |
| extra flag   | `31`                      |                      | `0x1f`   |
| command id   | `13`                      |                      | `0x0d`   |
| command size | `4`                       |                      | `0x04`   |
| start date   | `2023.12.23 00:00:00 GMT` | `0b0010111110010111` | `0x2f97` |
| channels     | `1`                       | `0b00000001`         | `0x01`   |
| days         | `1`                       |                      | `0x01`   |

Message hex dump with LRC: `1f 0d 04 2f 98 01 01 f4`


## Response

### Format

| Size   | Type                                               | Field                                            |
| ------ | -------------------------------------------------- | ------------------------------------------------ |
| `1`    | `uint8`                                            | extra flag = `0x1f`                              |
| `1`    | `uint8`                                            | command id = `0x0d`                              |
| `1`    | `uint8`                                            | command size (dynamic, `6+`)                     |
| `2`    | [packed date](../types.md#packed-date)             | [start date](#start-date)                        |
| `1..5` | [extended value](../types.md#extended-value)       | [channels bit set](../types.md#channels-bit-set) |
| `1`    | `uint8`                                            | [days](#days)                                    |
| `1`    | [pulse coefficient](../types.md#pulse-coefficient) | channel `1` pulse coefficient                    |
| `1..5` | [extended value](../types.md#extended-value)       | channel `1` day `1` value                        |
| `1..5` | [extended value](../types.md#extended-value)       | channel `1` day `2` value                        |
| `1`    | [pulse coefficient](../types.md#pulse-coefficient) | channel `2` pulse coefficient                    |
| `1..5` | [extended value](../types.md#extended-value)       | channel `2` day `1` value                        |
| `1..5` | [extended value](../types.md#extended-value)       | channel `2` day `2` value                        |
| ...    | ...                                                | ...                                              |
| `1`    | [pulse coefficient](../types.md#pulse-coefficient) | channel `N` pulse coefficient                    |
| `1..5` | [extended value](../types.md#extended-value)       | channel `N` day `D` value                        |
| `1..5` | [extended value](../types.md#extended-value)       | channel `N` day `D` value                        |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### **start date**

Start date for requested day pulse counter's values.
<br/>
[See details](../types.md#packed-date).

#### **channels bit set**

[See details](../types.md#channels-bit-set).

#### **days**

The number of days from archive.

It's pulse counter's values by days for each channel.

### Examples

#### 4th channel:

| Field                         | Value                     | Bits                                                                  | Hex      |
| ----------------------------- | ------------------------- | --------------------------------------------------------------------- | -------- |
| extra flag                    | `31`                      |                                                                       | `0x1f`   |
| command id                    | `13`                      |                                                                       | `0x0d`   |
| command size                  | `9`                       |                                                                       | `0x09`   |
| start date                    | `2023.12.23 00:00:00 GMT` | `0b10111011111011`                                                    | `0x2f97` |
| channels                      | `4`                       | `0b00001000`                                                          | `0x08`   |
| days                          | `2`                       |                                                                       | `0x02`   |
| channel `4` pulse coefficient | `100`                     | `0b10000011`                                                          | `0x83`   |
| channel `4` day `1` value     | `5524`                    | `0b0001010110010100`<br/>with extended bits:<br/>`0b1001010000101011` | `0x942b` |
| channel `4` day `2` value     | `5674`                    | `0b0001011000101010`<br/>with extended bits:<br/>`0b1010101000101100` | `0xaa2c` |

Message hex dump with LRC: `1f 0d 09 2f 97 08 02 83 94 2b aa 2c 46`


## See also

* [Packed date](../types.md#packed-date)
* [Extended value](../types.md#extended-value)
* [Channels bit set](../types.md#channels-bit-set)
