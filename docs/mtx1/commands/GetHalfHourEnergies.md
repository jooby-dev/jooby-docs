# GetHalfHourEnergies

Request/response to get energy with 30-minute accumulation period by selected energy type for date.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                                            |
| ---- | ------- | ---------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x6f`                                              |
| `1`  | `uint8` | command size = `5`                                               |
| `2`  | `uint8` | [packed date](../types.md#packed-date)                           |
| `1`  | `uint8` | [energy type](#energy-type)                                      |
| `2`  | `uint8` | index of the first requested record (valid index range `0 – 48`) |
| `1`  | `uint8` | number of requested records                                      |

### Parameters

#### energy type

| Value | Hex    | Energy type      |
| ----- | ------ | ---------------- |
| `1`   | `0x01` | `A+` (`1.8.0`)   |
| `2`   | `0x02` | `A-` (`2.8.0`)   |
| `4`   | `0x02` | `A+R+` (`3.5.0`) |
| `8`   | `0x02` | `A+R-` (`4.5.0`) |
| `16`  | `0x02` | `A-R+` (`5.5.0`) |
| `32`  | `0x02` | `A-R-` (`6.5.0`) |

### Examples

#### get A+ energy

| Field                                  | Value                               | Hex      |
| -------------------------------------- | ----------------------------------- | -------- |
| command id                             | `111`                               | `0x6f`   |
| command size                           | `5`                                 | `0x05`   |
| [packed date](../types.md#packed-date) | year: `2021`, month: `2`, date: `3` | `0x2a43` |
| [energy type](#energy-type)            | `A+`                                | `0x01`   |
| index of the first requested record    | `5`                                 | `0x0005` |
| number of requested records            | `10`                                | `0x0a`   |

Command hex dump: `6f 05 2a43 01 05 0a`


## Response

### Format

| Size  | Type                            | Field                                                      |
| ----- | ------------------------------- | ---------------------------------------------------------- |
| `1`   | `uint8`                         | command id = `0x6f`                                        |
| `1`   | `uint8`                         | command size = `5+`                                        |
| `2`   | `uint8`                         | [packed date](../types.md#packed-date)                     |
| `1`   | `uint8`                         | [energy type](#energy-type)                                |
| `1`   | `uint8`                         | index of the first requested record                        |
| `1`   | `uint8`                         | number of requested records                                |
| `2*n` | [tariff energy](#tariff-energy) | accumulated data, according to [energy type](#energy-type) |

> `n` - the number of energies derived from packed energy type field.

### Parameters

#### tariff energy

| Bit range | Field              | Description                                                        |
| --------- | ------------------ | ------------------------------------------------------------------ |
| `15..14`  | tariff             | tariff number `0..3`, extracted from the two most significant bits |
| `13..0`   | accumulated energy | `14`-bit value representing the actual accumulated measurement     |

An tariff energy value of `0xffff` indicates that no data is available because the meter was turned off.<br>

### Examples

#### get A+ energy

| Field                                  | Value                                | Hex      |
| -------------------------------------- | ------------------------------------ | -------- |
| command id                             | `111`                                | `0x6f`   |
| command size                           | `11`                                 | `0x0b`   |
| [packed date](../types.md#packed-date) | year: `2021`, month: `2`, date: `3`  | `0x2a43` |
| [energy type](#energy-type)            | `A+`                                 | `0x01`   |
| index of the first requested record    | `4`                                  | `0x04`   |
| number of requested records            | `3`                                  | `0x03`   |
| accumulated data `2:30-3:00`           | tariff: `T2`,  accumulated data:`16` | `0x4010` |
| accumulated data `3:00-3:30`           | tariff: `T2`,  accumulated data:`18` | `0x4012` |
| accumulated data `3:30-4:00`           | tariff: `T4`,  accumulated data:`17` | `0xc011` |

Command hex dump: `76 0b 2a43 01 04 03 4010 4012 c011`


## See also

* [Access level](../basics.md#command-access-level)
