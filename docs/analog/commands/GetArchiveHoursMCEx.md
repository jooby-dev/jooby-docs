# GetArchiveHoursMCEx

Command to request/receive hour pulse counter's values from device archive. This is an extended version of [GetArchiveHoursMC](./GetArchiveHoursMC.md) to get archive hours more than 8

## Request

### Format

| Size   | Type                                         | Field                                            |
| ------ | -------------------------------------------- | ------------------------------------------------ |
| `1`    | `byte`                                       | extra flag = `0x1f`                              |
| `1`    | `byte`                                       | command id = `0x30`                              |
| `1`    | `byte`                                       | command size (dynamic, `5+`)                     |
| `2`    | [packed date](../types.md#packed-date)       | [start date](#start-date)                        |
| `1`    | `byte`                                       | [hour](#hour)                                    |
| `1`    | `byte`                                       | [hours](#hours)                                  |
| `1..5` | [extended value](../types.md#extended-value) | [channels bit set](../types.md#channels-bit-set) |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **start date**

Start date for requested day pulse counter's values.
<br>
[See details](../types.md#packed-date).

#### **hour**

It's a start hour.

#### **hours**

Count the pulse counter's value with a diff for each previous hour. The hours value 0 means 1 hour.

#### **channels bit set**

[See details](../types.md#channels-bit-set).

### Examples

#### channels `1`, `3`, `4`:

| Field        | Value                     | Bits                 | Hex      |
| ------------ | ------------------------- | -------------------- | -------- |
| extra flag   | `31`                      |                      | `0x1f`   |
| command id   | `48`                      |                      | `0x30`   |
| command size | `5`                       |                      | `0x05`   |
| start date   | `2023.12.23 00:00:00 GMT` | `0b0010111110010111` | `0x2f97` |
| hours        | hour: `12:00`             | `0b00001100`         | `0x0c`   |
| hours        | hours: `2`                | `0b00000010`         | `0x02`   |
| channels     | `1`                       | `0b00000001`         | `0x01`   |

Message hex dump with LRC: `1f 30 05 2f 97 0c 02 01 c8`
## Response

### Format

| Size   | Type                                         | Field                                            |
| ------ | -------------------------------------------- | ------------------------------------------------ |
| `1`    | `byte`                                       | command id = `0x1a`                              |
| `1`    | `byte`                                       | command size (dynamic, `6+`)                     |
| `2`    | [packed date](../types.md#packed-date)       | [start date](#start-date)                        |
| `1`    | byte                                         | [hour](#hour)                                    |
| `1`    | byte                                         | [hours](#hours)                                  |
| `1..5` | [extended value](../types.md#extended-value) | [channels bit set](../types.md#channels-bit-set) |
| `1..5` | [extended value](../types.md#extended-value) | channel `1` hour `1` value                       |
| `1..5` | [extended value](../types.md#extended-value) | channel `1` hour `1` diff                        |
| `1..5` | [extended value](../types.md#extended-value) | channel `1` hour `2` diff                        |
| `1..5` | [extended value](../types.md#extended-value) | channel `2` hour `1` value                       |
| `1..5` | [extended value](../types.md#extended-value) | channel `2` hour `1` diff                        |
| `1..5` | [extended value](../types.md#extended-value) | channel `2` hour `2` diff                        |
| ...    | ...                                          | ...                                              |
| `1..5` | [extended value](../types.md#extended-value) | channel `N` hour `H` value                       |
| `1..5` | [extended value](../types.md#extended-value) | channel `N` hour `H` diff                        |
| `1..5` | [extended value](../types.md#extended-value) | channel `N` hour `H` diff                        |

It's a command with a [two-bytes header](../message.md#command-with-a-two-bytes-header).

### Parameters

#### **start date**

Start date for requested day pulse counter's values.
<br>
[See details](../types.md#packed-date).

#### **hour**

It's a start hour.

#### **hours**

Count the pulse counter's full value with a diff for each previous hour. The hours value 0 means 1 hour.

#### **channels bit set**

[See details](../types.md#channels-bit-set).

### Examples

#### first `4` channels:

| Field                      | Value                     | Bits                                                                | Hex      |
| -------------------------- | ------------------------- | ------------------------------------------------------------------- | -------- |
| extra flag                 | `31`                      |                                                                     | `0x1f`   |
| command id                 | `48`                      |                                                                     | `0x30`   |
| command size               | `14`                      |                                                                     | `0x0e`   |
| start date                 | `2023.12.23 00:00:00 GMT` | `0b0010111110010111`                                                | `0x2f97` |
| hours                      | hour: `12:00`             | `0b00001100`                                                        | `0x0c`   |
| hours                      | hours: `1`                | `0b00000000`                                                        | `0x01`   |
| channels                   | `1`, `2`, `3`, `4`        | `0b00001111`                                                        | `0x0f`   |
| channel `1` hour `1` value | `131`                     | `0b0000000010000011`<br>with extended bits:<br>`0b0000100000110001` | `0x8301` |
| channel `1` hour `1` diff  | `10`                      | `0b00001010`<br>with extended bits:<br>`0b00001010`                 | `0x0a`   |
| channel `2` hour `1` value | `8`                       | `0b00001000`<br>with extended bits:<br>`0b00001000`                 | `0x08`   |
| channel `2` hour `1` diff  | `10`                      | `0b00001010`<br>with extended bits:<br>`0b00001010`                 | `0x0a`   |
| channel `3` hour `1` value | `8`                       | `0b00001000`<br>with extended bits:<br>`0b00001000`                 | `0x08`   |
| channel `3` hour `1` diff  | `10`                      | `0b00001010`<br>with extended bits:<br>`0b00001010`                 | `0x0a`   |
| channel `4` hour `1` value | `12`                      | `0b00001000`<br>with extended bits:<br>`0b00001000`                 | `0x0c`   |
| channel `4` hour `1` diff  | `10`                      | `0b00001100`<br>with extended bits:<br>`0b00001100`                 | `0x0a`   |

Message hex dump with LRC: `1f 30 0e 2f 97 0c 01 0f 83 01 0a 08 0a 08 0a 0c 0a 40`


## See also

* [Packed date](../types.md#packed-date)
* [Extended value](../types.md#extended-value)
* [Channels bit set](../types.md#channels-bit-set)
