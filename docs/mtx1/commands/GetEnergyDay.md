# GetEnergyDay

Request/response to get day energy A+ by default or selected energy type for 4 tariffs (T1-T4) for date.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

#### case #1 without energy type

| Size | Type    | Field                                     |
| ---- | ------- | ----------------------------------------- |
| `1`  | `uint8` | command id = `0x16`                       |
| `1`  | `uint8` | command size = `3`                        |
| `1`  | `uint8` | year (number of years after `2000`)       |
| `1`  | `uint8` | month (`1` - January ... `12` - December) |
| `1`  | `uint8` | date                                      |

#### case #2 with energy type

| Size | Type    | Field                                                                                         |
| ---- | ------- | --------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x16`                                                                           |
| `1`  | `uint8` | command size = `4`                                                                            |
| `1`  | `uint8` | year (number of years after `2000`)                                                           |
| `1`  | `uint8` | month (`1` - January ... `12` - December)                                                     |
| `1`  | `uint8` | date                                                                                          |
| `1`  | `uint8` | energy type according to OBIS code <br/> `1` - `1.8.x`, `2` - `2.8.x` (where `x` is `1`..`4`) |

### Examples

#### request day values for 2024.03.22:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `22`  | `0x16` |
| command size | `3`   | `0x03` |
| year         | `24`  | `0x18` |
| month        | `3`   | `0x03` |
| date         | `22`  | `0x16` |

Message hex dump: `16 03 18 03 16`

#### request day values with energy type for 2024.03.22:

| Field        | Value                    | Hex    |
| ------------ | ------------------------ | ------ |
| command id   | `22`                     | `0x16` |
| command size | `4`                      | `0x04` |
| year         | `24`                     | `0x18` |
| month        | `3`                      | `0x03` |
| date         | `22`                     | `0x16` |
| energy type  | OBIS code `1.8.x` (`A+`) | `0x01` |

Message hex dump: `16 04 18 03 16 01`


## Response

### Format

#### response without energy type in request

| Size | Type    | Field                                                      |
| ---- | ------- | ---------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x16`                                        |
| `1`  | `uint8` | command size = `19`                                        |
| `1`  | `uint8` | year (number of years after `2000`)                        |
| `1`  | `uint8` | month (`1` - January ... `12` - December)                  |
| `1`  | `uint8` | date                                                       |
| `4`  | `int32` | active energy A+ (`1.8.1` – `1.8.4`) for tariffs `T1`-`T4` |

#### response with energy type in request

| Size | Type    | Field                                                                                                                                                                                                                                        |
| ---- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x16`                                                                                                                                                                                                                          |
| `1`  | `uint8` | command size (dynamic, `8+`, max is `20`)                                                                                                                                                                                                    |
| `1`  | `uint8` | year (number of years after `2000`)                                                                                                                                                                                                          |
| `1`  | `uint8` | month (`1` - January ... `12` - December)                                                                                                                                                                                                    |
| `1`  | `uint8` | date                                                                                                                                                                                                                                         |
| `1`  | `uint8` | packed energy type with tariff flags <br/> `BIT3`-`BIT0` - energy according to OBIS code (`1` - `1.8.x`, `2` - `2.8.x`) <br/> `BIT7`-`BIT4` tariffs with corresponding energies (`BIT4` - `T1`, `BIT5` - `T2`, `BIT6` - `T3`, `BIT7` - `T4`) |
| `1+` | `int32` | tariff energies (only when energy is not equal `0`)                                                                                                                                                                                          |

### Examples

#### default A+ energy:

| Field        | Value      | Hex          |
| ------------ | ---------- | ------------ |
| command id   | `22`       | `0x16`       |
| command size | `19`       | `0x13`       |
| year         | `24`       | `0x18`       |
| month        | `3`        | `0x03`       |
| date         | `22`       | `0x16`       |
| T1 energy    | `40301230` | `0x0266f2ae` |
| T2 energy    | `3334244`  | `0x0032e064` |
| T3 energy    | `2333`     | `0x0000091d` |
| T4 energy    | `2145623`  | `0x0020bd57` |

Message hex dump: `16 13 18 03 16 02 66 f2 ae 00 32 e0 64 00 00 09 1d 00 20 bd 57`

#### A- energy with 3 tariffs:

| Field        | Value      | Hex          |
| ------------ | ---------- | ------------ |
| command id   | `22`       | `0x16`       |
| command size | `16`       | `0x10`       |
| year         | `24`       | `0x18`       |
| month        | `3`        | `0x03`       |
| date         | `22`       | `0x16`       |
| T1 energy    | `40301230` | `0x0266f2ae` |
| T2 energy    | `null`     | -            |
| T3 energy    | `2333`     | `0x0000091d` |
| T4 energy    | `2145623`  | `0x0020bd57` |

Message hex dump: `16 10 18 03 16 d0 02 66 f2 ae 00 00 09 1d 00 20 bd 57`


## See also

* [Access level](../basics.md#command-access-level)
