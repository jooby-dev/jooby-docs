# GetEnergy

Request/response to get current energy `A+` by default or selected energy type for 4 tariffs (`T1-T4`).

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

#### case #1 without energy type

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x0f` |
| `1`  | `uint8` | command size = `0`  |

#### case #2 with energy type

| Size | Type    | Field                                                                                         |
| ---- | ------- | --------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x0f`                                                                           |
| `1`  | `uint8` | command size = `1`                                                                            |
| `1`  | `uint8` | energy type according to OBIS code <br/> `1` - `1.8.x`, `2` - `2.8.x` (`x`=`1`..`4`) |

### Examples

#### get default A+ energy:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `15`  | `0x0f` |
| command size | `0`   | `0x00` |

Command hex dump: `0f 00`

#### get A- energy:

| Field        | Value                    | Hex    |
| ------------ | ------------------------ | ------ |
| command id   | `15`                     | `0x0f` |
| command size | `1`                      | `0x01` |
| energy type  | OBIS code `2.8.x` (`A-`) | `0x02` |

Command hex dump: `0f 01 02`


## Response

### Format

#### response without energy type in request

| Size | Type    | Field                                                      |
| ---- | ------- | ---------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x0f`                                        |
| `1`  | `uint8` | command size = `16`                                        |
| `16` | `int32` | active energy A+ (`1.8.1` – `1.8.4`) for tariffs `T1`-`T4` |

#### response with energy type in request

| Size  | Type    | Field                                                                                                                                                                                                                                        |
| ----- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`   | `uint8` | command id = `0x0f`                                                                                                                                                                                                                          |
| `1`   | `uint8` | command size (dynamic, `5+`, max is `17`)                                                                                                                                                                                                    |
| `1`   | `uint8` | packed energy type with tariff flags <br/> `BIT3`-`BIT0` - energy according to OBIS code (`1` - `1.8.x`, `2` - `2.8.x`) <br/> `BIT7`-`BIT4` tariffs with corresponding energies (`BIT4` - `T1`, `BIT5` - `T2`, `BIT6` - `T3`, `BIT7` - `T4`) |
| `4*n` | `int32` | tariff energies (only when energy is not equal `0`)                                                                                                                                                                                          |

> `n` - the number of energies derived from packed energy type field.

### Examples

#### default A+ energy:

| Field        | Value      | Hex          |
| ------------ | ---------- | ------------ |
| command id   | `15`       | `0x0f`       |
| command size | `16`       | `0x10`       |
| `T1` energy  | `40301230` | `0x0266f2ae` |
| `T2` energy  | `3334244`  | `0x0032e064` |
| `T3` energy  | `2333`     | `0x0000091d` |
| `T4` energy  | `2145623`  | `0x0020bd57` |

Command hex dump: `0f 10 02 66 f2 ae 00 32 e0 64 00 00 09 1d 00 20 bd 57`

#### A- energy with 3 tariffs:

| Field                  | Value      | Hex          |
| ---------------------- | ---------- | ------------ |
| command id             | `15`       | `0x0f`       |
| command size           | `13`       | `0x0d`       |
| energy type with flags |            | `0xd0`       |
| `T1` energy            | `40301230` | `0x0266f2ae` |
| `T2` energy            | `null`     | -            |
| `T3` energy            | `2333`     | `0x0000091d` |
| `T4` energy            | `2145623`  | `0x0020bd57` |

Command hex dump: `0f 0d d0 02 66 f2 ae 00 00 09 1d 00 20 bd 57`


## See also

* [Access level](../basics.md#command-access-level)
