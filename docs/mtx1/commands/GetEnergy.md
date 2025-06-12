# GetEnergy

Request/response to get current active energy (`A+`) by default or selected energy type for all tariffs (`T1`-`T4`).

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

#### case #1: without energy type

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x0f` |
| `1`  | `uint8` | command size = `0`  |

#### case #2: with energy type

| Size | Type    | Field                       |
| ---- | ------- | --------------------------- |
| `1`  | `uint8` | command id = `0x0f`         |
| `1`  | `uint8` | command size = `1`          |
| `1`  | `uint8` | [energy type](#energy-type) |

### Parameters

#### energy type

| Energy type (x=`1`..`4`) | Value |
| ------------------------ | ----- |
| `A+` (`1.8.x`)           | `1`   |

### Examples

#### request the current active energy (`A+`)

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `15`  | `0x0f` |
| command size | `0`   | `0x00` |

Command hex dump: `16 01 00`

#### request the current active energy (`A+`) with energy type

| Field        | Value                      | Hex    |
| ------------ | -------------------------- | ------ |
| command id   | `15`                       | `0x0f` |
| command size | `1`                        | `0x01` |
| energy type  | `A+` (`1.8.x`, x=`1`..`4`) | `0x01` |

Command hex dump: `0f 01 01`


## Response

### Format

#### response to request without energy type

| Size | Type    | Field                                         |
| ---- | ------- | --------------------------------------------- |
| `1`  | `uint8` | command id = `0x0f`                           |
| `1`  | `uint8` | command size = `16`                           |
| `4`  | `int32` | active energy for tariff `T1`, `A+` (`1.8.1`) |
| `4`  | `int32` | active energy for tariff `T2`, `A+` (`1.8.2`) |
| `4`  | `int32` | active energy for tariff `T3`, `A+` (`1.8.3`) |
| `4`  | `int32` | active energy for tariff `T4`, `A+` (`1.8.4`) |

#### response with energy type in request

| Size  | Type    | Field                                                                                                                                                                                                     |
| ----- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`   | `uint8` | command id = `0x0f`                                                                                                                                                                                       |
| `1`   | `uint8` | command size (dynamic, `1+`, max is `17`)                                                                                                                                                                 |
| `1`   | `uint8` | packed energy type with tariff flags<br/> `BIT3`-`BIT0` - [energy type](#energy-type)<br/> `BIT7`-`BIT4` tariffs with corresponding energies (`BIT4` - `T1`, `BIT5` - `T2`, `BIT6` - `T3`, `BIT7` - `T4`) |
| `4*n` | `int32` | tariff energies (only when energy is not equal `0`)                                                                                                                                                       |

> `n` - the number of energies derived from packed energy type field.

### Examples

#### response to request without energy type

| Field          | Value      | Hex          |
| -------------- | ---------- | ------------ |
| command id     | `15`       | `0x0f`       |
| command size   | `16`       | `0x10`       |
| `A+` (`1.8.1`) | `40301230` | `0x0266f2ae` |
| `A+` (`1.8.2`) | `3334244`  | `0x0032e064` |
| `A+` (`1.8.3`) | `2333`     | `0x0000091d` |
| `A+` (`1.8.4`) | `2145623`  | `0x0020bd57` |

Command hex dump: `0f 10 02 66 f2 ae 00 32 e0 64 00 00 09 1d 00 20 bd 57`

#### response to request with energy type (`A+`)

| Field                  | Value                                                                                               | Hex          |
| ---------------------- | --------------------------------------------------------------------------------------------------- | ------------ |
| command id             | `15`                                                                                                | `0x0f`       |
| command size           | `13`                                                                                                | `0x0d`       |
| energy type with flags | energy: `A+` (`1.8.x`, x=`1`..`4`)<br>`T1`: `true`<br>`T2`: `false`<br>`T3`: `true`<br>`T4`: `true` | `0xd0`       |
| `A+` (`1.8.1`)         | `40301230`                                                                                          | `0x0266f2ae` |
| `A+` (`1.8.2`)         | `null`                                                                                              | -            |
| `A+` (`1.8.3`)         | `2333`                                                                                              | `0x0000091d` |
| `A+` (`1.8.4`)         | `2145623`                                                                                           | `0x0020bd57` |

Command hex dump: `0f 0d d0 02 66 f2 ae 00 00 09 1d 00 20 bd 57`


## See also

* [Access level](../basics.md#command-access-level)
