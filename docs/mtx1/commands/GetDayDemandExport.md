# GetDayDemandExport

Request/response to get daily energy (`A-`) by default or selected energy type for all tariffs (`T1`-`T4`) for date.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

#### case #1: without energy type

| Size | Type    | Field                                         |
| ---- | ------- | --------------------------------------------- |
| `1`  | `uint8` | command id = `0x4f`                           |
| `1`  | `uint8` | command size = `3`                            |
| `1`  | `uint8` | year (number of years after `2000`)           |
| `1`  | `uint8` | month (`1` - January ... `12` - December)     |
| `1`  | `uint8` | date (month day number which starts from `1`) |

#### case #2: with energy type

| Size | Type    | Field                                         |
| ---- | ------- | --------------------------------------------- |
| `1`  | `uint8` | command id = `0x4f`                           |
| `1`  | `uint8` | command size = `4`                            |
| `1`  | `uint8` | year (number of years after `2000`)           |
| `1`  | `uint8` | month (`1` - January ... `12` - December)     |
| `1`  | `uint8` | date (month day number which starts from `1`) |
| `1`  | `uint8` | [energy type](#energy-type)                   |

### Parameters

#### energy type

| Energy type (x=`1`..`4`) | Value |
| ------------------------ | ----- |
| `A+` (`1.8.x`)           | `1`   |
| `A-` (`2.8.x`)           | `2`   |

### Examples

#### request the daily active energy (`A-`) without energy type for 2024.03.22

| Field        | Value       | Hex    |
| ------------ | ----------- | ------ |
| command id   | `79`        | `0x4f` |
| command size | `3`         | `0x03` |
| year         | `24`        | `0x18` |
| month        | `3` (March) | `0x03` |
| date         | `22`        | `0x16` |

Command hex dump: `4f 03 18 03 16`

#### request the daily active energy (`A-`) with energy type for 2024.03.22

| Field        | Value                      | Hex    |
| ------------ | -------------------------- | ------ |
| command id   | `79`                       | `0x4f` |
| command size | `4`                        | `0x04` |
| year         | `24`                       | `0x18` |
| month        | `3` (March)                | `0x03` |
| date         | `22`                       | `0x16` |
| energy type  | `A+` (`1.8.x`, x=`1`..`4`) | `0x01` |

Command hex dump: `4f 04 18 03 16 01`


## Response

### Format

#### response to request without energy type

| Size | Type    | Field                                         |
| ---- | ------- | --------------------------------------------- |
| `1`  | `uint8` | command id = `0x16`                           |
| `1`  | `uint8` | command size = `19`                           |
| `1`  | `uint8` | year (number of years after `2000`)           |
| `1`  | `uint8` | month (`1` - January ... `12` - December)     |
| `1`  | `uint8` | date (month day number which starts from `1`) |
| `4`  | `int32` | active energy for tariff `T1`, `A-` (`2.8.1`) |
| `4`  | `int32` | active energy for tariff `T2`, `A-` (`2.8.2`) |
| `4`  | `int32` | active energy for tariff `T3`, `A-` (`2.8.3`) |
| `4`  | `int32` | active energy for tariff `T4`, `A-` (`2.8.4`) |

#### response to request with energy type

| Size  | Type    | Field                                                                                                                                                                                                    |
| ----- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`   | `uint8` | command id = `0x4f`                                                                                                                                                                                      |
| `1`   | `uint8` | command size (dynamic, `8+`, max is `20`)                                                                                                                                                                |
| `1`   | `uint8` | year (number of years after `2000`)                                                                                                                                                                      |
| `1`   | `uint8` | month (`1` - January ... `12` - December)                                                                                                                                                                |
| `1`   | `uint8` | date (month day number which starts from `1`)                                                                                                                                                            |
| `1`   | `uint8` | packed energy type with tariff flags <br/>`BIT3`-`BIT0` - [energy type](#energy-type)<br/>`BIT7`-`BIT4` tariffs with corresponding energies (`BIT4` - `T1`, `BIT5` - `T2`, `BIT6` - `T3`, `BIT7` - `T4`) |
| `4*n` | `int32` | tariff energies (only when energy is not equal `0`)                                                                                                                                                      |

> `n` - the number of energies derived from packed energy type field.

### Examples

#### response to request without energy type

| Field          | Value       | Hex          |
| -------------- | ----------- | ------------ |
| command id     | `79`        | `0x4f`       |
| command size   | `19`        | `0x13`       |
| year           | `24`        | `0x18`       |
| month          | `3` (March) | `0x03`       |
| date           | `22`        | `0x16`       |
| `A+` (`1.8.1`) | `40301230`  | `0x0266f2ae` |
| `A+` (`1.8.2`) | `3334244`   | `0x0032e064` |
| `A+` (`1.8.3`) | `2333`      | `0x0000091d` |
| `A+` (`1.8.4`) | `2145623`   | `0x0020bd57` |

Command hex dump: `4f 13 18 03 16 0266f2ae 0032e064 0000091d 0020bd57`

#### response to request with energy type (`A-`)

| Field                       | Value                                                                                               | Hex          |
| --------------------------- | --------------------------------------------------------------------------------------------------- | ------------ |
| command id                  | `79`                                                                                                | `0x16`       |
| command size                | `16`                                                                                                | `0x10`       |
| year                        | `24`                                                                                                | `0x18`       |
| month                       | `3` (March)                                                                                         | `0x03`       |
| date                        | `22`                                                                                                | `0x16`       |
| [energy type](#energy-type) | energy: `A-` (`2.8.x`, x=`1`..`4`)<br>`T1`: `true`<br>`T2`: `false`<br>`T3`: `true`<br>`T4`: `true` | `0xd2`       |
| `A-` (`1.8.1`)              | `40301230`                                                                                          | `0x0266f2ae` |
| `A-` (`1.8.2`)              | `null`                                                                                              | -            |
| `A-` (`1.8.3`)              | `2333`                                                                                              | `0x0000091d` |
| `A-` (`1.8.4`)              | `2145623`                                                                                           | `0x0020bd57` |

Command hex dump: `4f 10 18 03 16 d2 0266f2ae 0000091d 0020bd57`


## See also

* [Access level](../basics.md#command-access-level)
