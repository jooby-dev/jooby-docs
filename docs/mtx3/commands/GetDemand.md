# GetDemand

Request/response to get the measurement data by selected type for date.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

#### case #1

| Size | Type     | Field                                                                         |
| ---- | -------- | ----------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x76`                                                           |
| `1`  | `uint8`  | command size = `7`                                                            |
| `2`  | `uint8`  | [packed date](../../types.md#packed-date)                                     |
| `1`  | `uint8`  | [demand type](#demand-type)                                                   |
| `2`  | `uint16` | index of the first requested record ([valid index range](#valid-index-range)) |
| `1`  | `uint8`  | number of requested records                                                   |
| `1`  | `uint8`  | accumulation period `1/3/5/10/15/30/60`                                       |

#### case #2: request for the repeated hour during the daylight saving time change

| Size | Type     | Field                                                                                              |
| ---- | -------- | -------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x76`                                                                                |
| `1`  | `uint8`  | command size = `7`                                                                                 |
| `2`  | `uint8`  | [packed date](../../types.md#packed-date)                                                          |
| `1`  | `uint8`  | [demand type](#demand-type)                                                                        |
| `2`  | `uint16` | index of the first requested record ([valid index range](#valid-index-range))                      |
| `1`  | `uint8`  | number of requested records ([daylight saving time parameters](#daylight- saving-time-parameters)) |
| `1`  | `uint8`  | accumulation period `1/3/5/10/15/30/60`                                                            |

### Parameters

#### **demand type**

| Value | Hex    | Demand type  (x=`1`..`4`)                                           |
| ----- | ------ | ------------------------------------------------------------------- |
| `1`   | `0x01` | `1/3/5/10/15/30/60`-minute active energy for phase `A`, `A+`        |
| `2`   | `0x02` | `1/3/5/10/15/30/60`-minute active energy for phase `B`, `A+`        |
| `3`   | `0x03` | `1/3/5/10/15/30/60`-minute active energy for phase `C`, `A+`        |
| `4`   | `0x04` | `1/3/5/10/15/30/60`-minute active energy for phase `A`, `A-`        |
| `5`   | `0x05` | `1/3/5/10/15/30/60`-minute active energy for phase `B`, `A-`        |
| `6`   | `0x06` | `1/3/5/10/15/30/60`-minute active energy for phase `C`, `A-`        |
| `7`   | `0x07` | `1/3/5/10/15/30/60`-minute active energy for phase `A`, `A+R+`      |
| `8`   | `0x08` | `1/3/5/10/15/30/60`-minute active energy for phase `B`, `A+R+`      |
| `9`   | `0x09` | `1/3/5/10/15/30/60`-minute active energy for phase `C`, `A+R+`      |
| `10`  | `0x0a` | `1/3/5/10/15/30/60`-minute active energy for phase `A`, `A+R-`      |
| `11`  | `0x0b` | `1/3/5/10/15/30/60`-minute active energy for phase `B`, `A+R-`      |
| `12`  | `0x0c` | `1/3/5/10/15/30/60`-minute active energy for phase `C`, `A+R-`      |
| `13`  | `0x0d` | `1/3/5/10/15/30/60`-minute active energy for phase `A`, `A-R+`      |
| `14`  | `0x0e` | `1/3/5/10/15/30/60`-minute active energy for phase `B`, `A-R+`      |
| `15`  | `0x0f` | `1/3/5/10/15/30/60`-minute active energy for phase `C`, `A-R+`      |
| `16`  | `0x10` | `1/3/5/10/15/30/60`-minute active energy for phase `A`, `A-R-`      |
| `17`  | `0x11` | `1/3/5/10/15/30/60`-minute active energy for phase `B`, `A-R-`      |
| `18`  | `0x12` | `1/3/5/10/15/30/60`-minute active energy for phase `C`, `A-R-`      |
| `19`  | `0x13` | `1/3/5/10/15/30/60`-minute active energy for phase `A`, `R+`        |
| `20`  | `0x14` | `1/3/5/10/15/30/60`-minute active energy for phase `B`, `R+`        |
| `21`  | `0x15` | `1/3/5/10/15/30/60`-minute active energy for phase `C`, `R+`        |
| `22`  | `0x16` | `1/3/5/10/15/30/60`-minute active energy for phase `A`, `R-`        |
| `23`  | `0x17` | `1/3/5/10/15/30/60`-minute active energy for phase `B`, `R-`        |
| `24`  | `0x18` | `1/3/5/10/15/30/60`-minute active energy for phase `C`, `R-`        |
| `25`  | `0x19` | `1/3/5/10/15/30/60`-minute voltage for phase `A`,                   |
| `26`  | `0x1a` | `1/3/5/10/15/30/60`-minute voltage for phase `B`,                   |
| `27`  | `0x1b` | `1/3/5/10/15/30/60`-minute voltage for phase `C`,                   |
| `28`  | `0x1c` | `10`-minute voltage for phase `A`                                   |
| `29`  | `0x1d` | `10`-minute voltage for phase `B`                                   |
| `30`  | `0x1e` | `10`-minute voltage for phase `C`                                   |
| `31`  | `0x1f` | `1/3/5/10/15/30/60`-minute current for phase `A`                    |
| `32`  | `0x20` | `1/3/5/10/15/30/60`-minute current for phase `B`                    |
| `33`  | `0x21` | `1/3/5/10/15/30/60`-minute current for phase `C`                    |
| `129` | `0x81` | `1/3/5/10/15/30/60`-minute active energy, `А+` (`1.4.0`)            |
| `130` | `0x82` | `1/3/5/10/15/30/60`-minute active energy, `А-` (`2.4.0`)            |
| `131` | `0x84` | `1/3/5/10/15/30/60`-minute reactive energy `A+R+`, (3.4.0 7.4.0)    |
| `132` | `0x88` | `1/3/5/10/15/30/60`-minute reactive energy `A+R-`, (4.4.0 8.4.0)    |
| `144` | `0x90` | `1/3/5/10/15/30/60`-minute reactive energy `A-R+`, (5.4.0)          |
| `160` | `0xa0` | `1/3/5/10/15/30/60`-minute reactive energy `A-R-`, (6.4.0)          |
| `176` | `0xb0` | [archive channel 1](./GetOperatorParametersExt2.md#archive-channel) |
| `177` | `0xb1` | [archive channel 2](./GetOperatorParametersExt2.md#archive-channel) |
| `178` | `0xb2` | [archive channel 3](./GetOperatorParametersExt2.md#archive-channel) |
| `179` | `0xb3` | [archive channel 4](./GetOperatorParametersExt2.md#archive-channel) |
| `17a` | `0xb4` | [archive channel 5](./GetOperatorParametersExt2.md#archive-channel) |
| `17b` | `0xb5` | [archive channel 6](./GetOperatorParametersExt2.md#archive-channel) |

#### **valid index range**

| Accumulation Period (minutes) | Valid Index Range |
| ----------------------------- | ----------------- |
| `1`                           | `0..1440`         |
| `3`                           | `0..480`          |
| `5`                           | `0..288`          |
| `10`                          | `0..144`          |
| `15`                          | `0..96`           |
| `30`                          | `0..48`           |
| `60`                          | `0..24`           |

#### **daylight saving time parameters**

| Accumulation Period (minutes) | Index of the first requested record | Number of requested records |
| ----------------------------- | ----------------------------------- | --------------------------- |
| `1`                           | `1440`                              | `61`                        |
| `3`                           | `480`                               | `21`                        |
| `5`                           | `288`                               | `13`                        |
| `10`                          | `144`                               | `7`                         |
| `15`                          | `96`                                | `5`                         |
| `30`                          | `48`                                | `3`                         |
| `60`                          | `24`                                | `2`                         |

### Examples

#### get A+ energy

| Field                                     | Value                               | Hex      |
| ----------------------------------------- | ----------------------------------- | -------- |
| command id                                | `118`                               | `0x76`   |
| command size                              | `7`                                 | `0x07`   |
| [packed date](../../types.md#packed-date) | year: `2021`, month: `2`, date: `3` | `0x2a43` |
| [demand type](#demand-type)               | active energy for phase `A`, `A+`   | `0x01`   |
| index of the first requested record       | `5`                                 | `0x0005` |
| number of requested records               | `10`                                | `0x0a`   |
| accumulation period                       | `15`                                | `0x0f`   |

Command hex dump: `76 07 2a43 01 0005 0a 0f`

#### get A- energy for the repeated hour during the daylight saving time change

| Field                                     | Value                                | Hex      |
| ----------------------------------------- | ------------------------------------ | -------- |
| command id                                | `118`                                | `0x76`   |
| command size                              | `7`                                  | `0x07`   |
| [packed date](../../types.md#packed-date) | year: `2024`, month: `5`, date: `27` | `0x30bb` |
| [demand type](#demand-type)               | active energy for phase `B`, `A+`    | `0x02`   |
| index of the first requested record       | `48`                                 | `0x0030` |
| number of requested records               | `3`                                  | `0x03`   |
| accumulation period                       | `30`                                 | `0x1e`   |

Command hex dump: `76 07 30bb 02 0030 03 1e`

## Response

### Format

#### case #1

| Size  | Type     | Field                                                                         |
| ----- | -------- | ----------------------------------------------------------------------------- |
| `1`   | `uint8`  | command id = `0x76`                                                           |
| `1`   | `uint8`  | command size = `7+`                                                           |
| `2`   | `uint8`  | [packed date](../../types.md#packed-date)                                     |
| `1`   | `uint8`  | [demand type](#demand-type)                                                   |
| `2`   | `uint16` | index of the first requested record ([valid index range](#valid-index-range)) |
| `1`   | `uint8`  | number of requested records                                                   |
| `1`   | `uint8`  | accumulation period `1/3/5/10/15/30/60`                                       |
| `2*n` | uint16`  | accumulated data, according to [demand type](#demand-type)                    |

> `n` - the number of energies derived from packed energy type field.
>
#### case #2

Response with repeated hour during the daylight saving time change.

| Size  | Type                                  | Field                                                                         |
| ----- | ------------------------------------- | ----------------------------------------------------------------------------- |
| `1`   | `uint8`                               | command id = `0x76`                                                           |
| `1`   | `uint8`                               | command size = `7+`                                                           |
| `2`   | `uint8`                               | [packed date](../../types.md#packed-date)                                     |
| `1`   | `uint8`                               | [demand type](#demand-type)                                                   |
| `2`   | `uint16`                              | index of the first requested record ([valid index range](#valid-index-range)) |
| `1`   | `uint8`                               | number of requested records                                                   |
| `1`   | `uint8`                               | accumulation period `1/3/5/10/15/30/60`                                       |
| `2*n` | [accumulated data](#accumulated-data) | accumulated data, according to [demand type](#demand-type)                    |
| `1`   | `uint8`                               | the repeated hour during the daylight saving time change                      |
| `1`   | `uint8`                               | reserved                                                                      |

> `n` - the number of records derived from packed [demand type](#demand-type) field.

### Parameters

#### **accumulated-data**

If accumulation period is less then `60` and [demand type](#demand-type) is `A+` or `A-` then tariff included into accumulated data.

| Bit range | Field              | Description                                                        |
| --------- | ------------------ | ------------------------------------------------------------------ |
| `15..14`  | tariff             | tariff number `0..3`, extracted from the two most significant bits |
| `13..0`   | accumulated energy | `14`-bit value representing the actual accumulated measurement     |

### Examples

#### get A+ energy

| Field                                     | Value                               | Hex      |
| ----------------------------------------- | ----------------------------------- | -------- |
| command id                                | `118`                               | `0x76`   |
| command size                              | `15`                                | `0x0f`   |
| [packed date](../../types.md#packed-date) | year: `2021`, month: `2`, date: `3` | `0x2a43` |
| [demand type](#demand-type)               | active energy for phase `A`, `A+`   | `0x01`   |
| index of the first requested record       | `4`                                 | `0x0004` |
| number of requested records               | `3`                                 | `0x03`   |
| accumulation period                       | `15`                                | `0x0f`   |
| accumulated data `1:00-1:15`              | `16`                                | `0x0010` |
| accumulated data `1:15-1:30`              | `18`                                | `0x0012` |
| accumulated data `1:30-1:45`              | `17`                                | `0x0011` |

Command hex dump: `76 0f 2a43 01 0004 03 0f 0010 0012 0011`

#### get A- energy for the repeated hour during the daylight saving time change

| Field                                                    | Value                                | Hex      |
| -------------------------------------------------------- | ------------------------------------ | -------- |
| command id                                               | `118`                                | `0x76`   |
| command size                                             | `13`                                 | `0x08`   |
| [packed date](../../types.md#packed-date)                | year: `2024`, month: `5`, date: `27` | `0x30bb` |
| [demand type](#demand-type)                              | active energy for phase `B`, `A+`    | `0x02`   |
| index of the first requested record                      | `48`                                 | `0x0030` |
| number of requested records                              | `3`                                  | `0x03`   |
| accumulation period                                      | `30`                                 | `0x1e`   |
| accumulated data `0:00-0:30`                             | `16`                                 | `0x0010` |
| accumulated data `0:30-1:00`                             | `18`                                 | `0x0012` |
| the repeated hour during the daylight saving time change | `3`                                  | `0x03`   |
| reserved                                                 | `15`                                 | `0xff`   |

Command hex dump: `76 0d 30bb 02 0030 03 1e 0010 0012 03 ff`


## See also

* [Access level](../basics.md#command-access-level)
