# GetDemandCumulative

Request/response to get the cumulative measurement data by selected type for date.

Unlike [GetDemand](./GetDemand.md), which returns the relative value consumed during a measurement period, `GetDemandCumulative` returns the cumulative (absolute) value, regardless of tariff.

Supported only for `15`, `30`, and `60`-minute measurement periods.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

#### case #1

| Size | Type     | Field                                                                         |
| ---- | -------- | ----------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x77`                                                           |
| `1`  | `uint8`  | command size = `7`                                                            |
| `2`  | `uint8`  | [packed date](../types.md#packed-date)                                        |
| `1`  | `uint8`  | [demand type](#demand-type)                                                   |
| `2`  | `uint16` | index of the first requested record ([valid index range](#valid-index-range)) |
| `1`  | `uint8`  | number of requested records                                                   |
| `1`  | `uint8`  | accumulation period `15/30/60`                                                |

#### case #2: request for the repeated hour during the daylight saving time change

| Size | Type     | Field                                                                         |
| ---- | -------- | ----------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x77`                                                           |
| `1`  | `uint8`  | command size = `7`                                                            |
| `2`  | `uint8`  | [packed date](../types.md#packed-date)                                        |
| `1`  | `uint8`  | [demand type](#demand-type)                                                   |
| `2`  | `uint16` | index of the first requested record ([valid index range](#valid-index-range)) |
| `1`  | `uint8`  | number of requested records                                                   |
| `1`  | `uint8`  | accumulation period `15/30/60`                                                |

### Parameters

#### demand type

| Value | Hex    | Demand type  (x=`1`..`4`) |
| ----- | ------ | ------------------------- |
| `1`   | `0x01` | `A+` (`1.5.x`)            |
| `2`   | `0x02` | `A-` (`2.5.x`)            |

#### valid index range

| Accumulation Period (minutes) | Valid Index Range |
| ----------------------------- | ----------------- |
| `15`                          | `0..96`           |
| `30`                          | `0..48`           |
| `60`                          | `0..24`           |

#### daylight saving time parameters

| Accumulation Period (minutes) | Index of the first requested record | Number of requested records |
| ----------------------------- | ----------------------------------- | --------------------------- |
| `15`                          | `96`                                | `5`                         |
| `30`                          | `48`                                | `3`                         |
| `60`                          | `24`                                | `2`                         |

### Examples

#### get A+ energy

| Field                                  | Value                               | Hex      |
| -------------------------------------- | ----------------------------------- | -------- |
| command id                             | `119`                               | `0x77`   |
| command size                           | `7`                                 | `0x07`   |
| [packed date](../types.md#packed-date) | year: `2021`, month: `2`, date: `3` | `0x2a43` |
| [demand type](#demand-type)            | `A+`                                | `0x01`   |
| index of the first requested record    | `5`                                 | `0x0005` |
| number of requested records            | `10`                                | `0x0a`   |
| accumulation period                    | `15`                                | `0x0f`   |

Command hex dump: `77 07 2a43 01 0005 0a 0f`

#### get A- energy for the repeated hour during the daylight saving time change

| Field                                  | Value                                | Hex      |
| -------------------------------------- | ------------------------------------ | -------- |
| command id                             | `119`                                | `0x77`   |
| command size                           | `7`                                  | `0x07`   |
| [packed date](../types.md#packed-date) | year: `2024`, month: `5`, date: `27` | `0x30bb` |
| [demand type](#demand-type)            | `A-`                                 | `0x02`   |
| index of the first requested record    | `48`                                 | `0x0030` |
| number of requested records            | `3`                                  | `0x03`   |
| accumulation period                    | `30`                                 | `0x1e`   |

Command hex dump: `77 07 30bb 02 0030 03 1e`

## Response

### Format

#### case #1

| Size  | Type     | Field                                                                         |
| ----- | -------- | ----------------------------------------------------------------------------- |
| `1`   | `uint8`  | command id = `0x77`                                                           |
| `1`   | `uint8`  | command size = `7+`                                                           |
| `2`   | `uint8`  | [packed date](../types.md#packed-date)                                        |
| `1`   | `uint8`  | [demand type](#demand-type)                                                   |
| `2`   | `uint16` | index of the first requested record ([valid index range](#valid-index-range)) |
| `1`   | `uint8`  | number of requested records                                                   |
| `1`   | `uint8`  | accumulation period `15/30/60`                                                |
| `4*n` | `uint32` | accumulated data, according to [demand type](#demand-type)                    |

> `n` - the number of energies derived from packed energy type field.

#### case #2

Response with repeated hour during the daylight saving time change.

| Size  | Type             | Field                                                                         |
| ----- | ---------------- | ----------------------------------------------------------------------------- |
| `1`   | `uint8`          | command id = `0x77`                                                           |
| `1`   | `uint8`          | command size = `7+`                                                           |
| `2`   | `uint8`          | [packed date](../types.md#packed-date)                                        |
| `1`   | `uint8`          | [demand type](#demand-type)                                                   |
| `2`   | `uint16`         | index of the first requested record ([valid index range](#valid-index-range)) |
| `1`   | `uint8`          | number of requested records                                                   |
| `1`   | `uint8`          | accumulation period `15/30/60`                                                |
| `4*n` | `uint32`         | accumulated data, according to [demand type](#demand-type)                    |
| `1`   | `uint8`          | the repeated hour during the daylight saving time change                      |
| `1`   | `uint8`          | reserved                                                                      |

> `n` - the number of records derived from packed [demand type](#demand-type) field.

### Parameters

### Examples

#### get A+ energy

| Field                                  | Value                               | Hex          |
| -------------------------------------- | ----------------------------------- | ------------ |
| command id                             | `119`                               | `0x77`       |
| command size                           | `19`                                | `0x13`       |
| [packed date](../types.md#packed-date) | year: `2021`, month: `2`, date: `3` | `0x2a43`     |
| [demand type](#demand-type)            | `A+`                                | `0x01`       |
| index of the first requested record    | `4`                                 | `0x0004`     |
| number of requested records            | `3`                                 | `0x03`       |
| accumulation period                    | `15`                                | `0x0f`       |
| accumulated data `1:00-1:15`           | `16`                                | `0x00000010` |
| accumulated data `1:15-1:30`           | `34`                                | `0x00000022` |
| accumulated data `1:30-1:45`           | `51`                                | `0x00000033` |

Command hex dump: `77 13 2a43 01 0004 03 0f 00000010 00000022 00000033`

#### get A- energy for the repeated hour during the daylight saving time change

| Field                                                    | Value                                | Hex          |
| -------------------------------------------------------- | ------------------------------------ | ------------ |
| command id                                               | `119`                                | `0x77`       |
| command size                                             | `17`                                 | `0x11`       |
| [packed date](../types.md#packed-date)                   | year: `2024`, month: `5`, date: `27` | `0x30bb`     |
| [demand type](#demand-type)                              | `A-`                                 | `0x02`       |
| index of the first requested record                      | `48`                                 | `0x0030`     |
| number of requested records                              | `3`                                  | `0x03`       |
| accumulation period                                      | `30`                                 | `0x1e`       |
| accumulated data `0:00-0:30`                             | `16`                                 | `0x00000010` |
| accumulated data `0:30-1:00`                             | `34`                                 | `0x00000022` |
| the repeated hour during the daylight saving time change | `3`                                  | `0x03`       |
| reserved                                                 | `15`                                 | `0xff`       |

Command hex dump: `77 11 30bb 02 0030 03 1e 00000010 00000022 03 ff`


## See also

* [Access level](../basics.md#command-access-level)
* [GetDemand](./GetDemand.md)
