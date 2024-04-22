# GetExAbsArchiveHoursMC

Command to request hourly consumption (absolute values) of device channels from the archive.


## Request

### Format

| Size   | Type                                         | Field                                                      |
| ------ | -------------------------------------------- | ---------------------------------------------------------- |
| `1`    | `uint8`                                      | extra flag = `0x1f`                                        |
| `1`    | `uint8`                                      | command id = `0x0c`                                        |
| `1`    | `uint8`                                      | command size (dynamic, `4+`)                               |
| `2`    | [packed date](../types.md#packed-date)       | [start date](#start-date)                                  |
| `1`    | [packed hours](../types.md#packed-hours)     | [hours](#hours)                                            |
| `1..5` | [extended value](../types.md#extended-value) | [channels bit set](../parameter-types.md#channels-bit-set) |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### **start date**

Start date for requested day pulse counter's values.
<br/>
[See details](../types.md#packed-date).

#### **hours**

It`s full value of pulse counter with diff for each previous hours (8 hours if reporting data interval is set to 4 hours)
<br/>
[See details](../types.md#packed-hours).

#### **channels bit set**

[See details](../parameter-types.md#channels-bit-set).

### Examples

#### `1` channel:

| Field        | Value                     | Bits                 | Hex      |
| ------------ | ------------------------- | -------------------- | -------- |
| extra flag   | `31`                      |                      | `0x1f`   |
| command id   | `12`                      |                      | `0x0c`   |
| command size | `4`                       |                      | `0x04`   |
| start date   | `2023.12.23 00:00:00 GMT` | `0b0010111110010111` | `0x2f97` |
| hours        | hour: `12:00`, hours: `2` | `0b00101100`         | `0x2c`   |
| channels     | `1`                       | `0b00000001`         | `0x01`   |

Message hex dump with LRC: `1f 0c 04 2f 97 0c 01 f7`


## Response

### Format

| Size   | Type                                               | Field                                                      |
| ------ | -------------------------------------------------- | ---------------------------------------------------------- |
| `1`    | `uint8`                                            | extra flag = `0x1f`                                        |
| `1`    | `uint8`                                            | command id = `0x0c`                                        |
| `1`    | `uint8`                                            | command size (dynamic, `6+`)                               |
| `2`    | [packed date](../types.md#packed-date)             | [start date](#start-date)                                  |
| `1`    | [packed hours](../types.md#packed-hours)           | [hours](#hours)                                            |
| `1..5` | [extended value](../types.md#extended-value)       | [channels bit set](../parameter-types.md#channels-bit-set) |
| `1`    | [pulse coefficient](../types.md#pulse-coefficient) | channel `1` pulse coefficient                              |
| `1..5` | [extended value](../types.md#extended-value)       | channel `1` hour `1` value                                 |
| `1..5` | [extended value](../types.md#extended-value)       | channel `1` hour `1` diff                                  |
| `1..5` | [extended value](../types.md#extended-value)       | channel `1` hour `2` diff                                  |
| `1`    | [pulse coefficient](../types.md#pulse-coefficient) | channel `2` pulse coefficient                              |
| `1..5` | [extended value](../types.md#extended-value)       | channel `2` hour `1` value                                 |
| `1..5` | [extended value](../types.md#extended-value)       | channel `2` hour `1` diff                                  |
| `1..5` | [extended value](../types.md#extended-value)       | channel `2` hour `2` diff                                  |
| ...    | ...                                                | ...                                                        |
| `1`    | [pulse coefficient](../types.md#pulse-coefficient) | channel `N` pulse coefficient                              |
| `1..5` | [extended value](../types.md#extended-value)       | channel `N` hour `H` value                                 |
| `1..5` | [extended value](../types.md#extended-value)       | channel `N` hour `H` diff                                  |
| `1..5` | [extended value](../types.md#extended-value)       | channel `N` hour `H` diff                                  |

It's a command with a [three-bytes header](../message.md#command-with-a-three-bytes-header).

### Parameters

#### **start date**

Start date for requested day pulse counter's values.
<br/>
[See details](../types.md#packed-date).

#### **hours**

It`s full value of pulse counter with diff for each previous hours (8 hours if reporting data interval is set to 4 hours)
<br/>
[See details](../types.md#packed-hours).

#### **channels bit set**

[See details](../parameter-types.md#channels-bit-set).

### Examples

#### `1` channel:

| Field                         | Value                     | Bits                                                                                                  | Hex        |
| ----------------------------- | ------------------------- | ----------------------------------------------------------------------------------------------------- | ---------- |
| extra flag                    | `31`                      |                                                                                                       | `0x1f`     |
| command id                    | `12`                      |                                                                                                       | `0x0c`     |
| command size                  | `10`                      |                                                                                                       | `0x0a`     |
| start date                    | `2023.12.23 00:00:00 GMT` | `0b0010111110010111`                                                                                  | `0x2f97`   |
| hours                         | hour: `12:00`, hours: `2` | `0b00101100`                                                                                          | `0x2c`     |
| channels                      | `1`                       | `0b00000001`                                                                                          | `0x01`     |
| channel `1` pulse coefficient | `100`                     | `0b10000011`                                                                                          | `0x83`     |
| channel `1` hour `1` value    | `342457`                  | `0b00000000000001010011100110111001`<br/>with extended bits:<br/>`0b00000000101110011111001100010100` | `0xb9f314` |
| channel `1` hour `1` diff     | `128`                     | `0b0000000010000000`<br/>with extended bits:<br/>`0b1000000000000001`                                 | `0x8001`   |

Message hex dump with LRC: `1f 0c 0a 2f 97 2c 01 83 b9 f3 14 80 01 85`


## See also

* [Packed date](../types.md#packed-date)
* [Packed hours](../types.md#packed-hours)
* [Extended value](../types.md#extended-value)
* [Channels bit set](../parameter-types.md#channels-bit-set)
