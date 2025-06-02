# GetExportEnergyDayPrevious

Request/response to get the previous day energy `A-` for `4` tariffs (`T1-T4`).

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

#### case #1 without energy type

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x50` |
| `1`  | `uint8` | command size = `0`  |

#### case #2 with energy type

| Size | Type    | Field                                                                                         |
| ---- | ------- | --------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x50`                                                                           |
| `1`  | `uint8` | command size = `1`                                                                            |
| `1`  | `uint8` | energy type according to OBIS code <br/> `1` - `1.8.x`, `2` - `2.8.x` (`x`=`1`..`4`) |

### Examples

#### request the previous day `A-` energy without energy type

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `80`  | `0x50` |
| command size | `0`   | `0x00` |

Command hex dump: `50 00`

#### request the previous day `A+` energy with energy type

| Field        | Value                    | Hex    |
| ------------ | ------------------------ | ------ |
| command id   | `80`                     | `0x50` |
| command size | `1`                      | `0x04` |
| energy type  | OBIS code `1.8.x` (`A+`) | `0x01` |

Command hex dump: `50 01 01`

#### request the previous day `A-` energy with energy type

| Field        | Value                    | Hex    |
| ------------ | ------------------------ | ------ |
| command id   | `80`                     | `0x50` |
| command size | `1`                      | `0x04` |
| energy type  | OBIS code `2.8.x` (`A+`) | `0x02` |

Command hex dump: `50 01 02`


## Response

### Format

#### response without energy type in request

| Size | Type    | Field                                                 |
| ---- | ------- | ----------------------------------------------------- |
| `1`  | `uint8` | command id = `0x50`                                   |
| `1`  | `uint8` | command size = `16`                                   |
| `4`  | `int32` | energy `A-` (`2.8.1` – `2.8.4`) for tariffs `T1`-`T4` |

#### response with energy type in request

| Size  | Type    | Field                                                                                                                                                                                                                                        |
| ----- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`   | `uint8` | command id = `0x50`                                                                                                                                                                                                                          |
| `1`   | `uint8` | command size (dynamic, `8+`, max is `20`)                                                                                                                                                                                                    |
| `1`   | `uint8` | year (number of years after `2000`)                                                                                                                                                                                                          |
| `1`   | `uint8` | month (`1` - January ... `12` - December)                                                                                                                                                                                                    |
| `1`   | `uint8` | date (month day number which starts from `1`)                                                                                                                                                                                                |
| `1`   | `uint8` | packed energy type with tariff flags <br/> `BIT3`-`BIT0` - energy according to OBIS code (`1` - `1.8.x`, `2` - `2.8.x`) <br/> `BIT7`-`BIT4` tariffs with corresponding energies (`BIT4` - `T1`, `BIT5` - `T2`, `BIT6` - `T3`, `BIT7` - `T4`) |
| `4*n` | `int32` | tariff energies (only when energy is not equal `0`)                                                                                                                                                                                          |

> `n` - the number of energies derived from packed energy type field.

### Examples

#### default A- energy:

| Field        | Value       | Hex          |
| ------------ | ----------- | ------------ |
| command id   | `80`        | `0x50`       |
| command size | `19`        | `0x13`       |
| year         | `24`        | `0x18`       |
| month        | `3` (March) | `0x03`       |
| date         | `22`        | `0x16`       |
| `T1` energy  | `40301230`  | `0x0266f2ae` |
| `T2` energy  | `3334244`   | `0x0032e064` |
| `T3` energy  | `2333`      | `0x0000091d` |
| `T4` energy  | `2145623`   | `0x0020bd57` |

Command hex dump: `50 13 18 03 16 0266f2ae 0032e064 0000091d 0020bd57`

#### A- energy with 3 tariffs:

| Field        | Value                                                                               | Hex          |
| ------------ | ----------------------------------------------------------------------------------- | ------------ |
| command id   | `80`                                                                                | `0x50`       |
| command size | `16`                                                                                | `0x10`       |
| year         | `24`                                                                                | `0x18`       |
| month        | `3` (March)                                                                         | `0x03`       |
| date         | `22`                                                                                | `0x16`       |
| energy type  | OBIS code: `2.8.x`<br>`T1`: `true`<br>`T2`: `true`<br>`T3`: `false`<br>`T4`: `true` | `0xd2`       |
| `T1` energy  | `40301230`                                                                          | `0x0266f2ae` |
| `T2` energy  | `null`                                                                              | -            |
| `T3` energy  | `2333`                                                                              | `0x0000091d` |
| `T4` energy  | `2145623`                                                                           | `0x0020bd57` |

Command hex dump: `50 10 18 03 16 d2 0266f2ae 0000091d 0020bd57`


## See also

* [Access level](../basics.md#command-access-level)
