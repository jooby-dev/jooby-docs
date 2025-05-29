# GetDayMaxDemand

Request/response to get the maximum daily power `P+` for all tariffs (`T1`-`T4`).

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                         |
| ---- | ------- | --------------------------------------------- |
| `1`  | `uint8` | command id = `0x31`                           |
| `1`  | `uint8` | command size = `3`                            |
| `1`  | `uint8` | year (number of years after `2000`)           |
| `1`  | `uint8` | month (`1` - January ... `12` - December)     |
| `1`  | `uint8` | date (month day number which starts from `1`) |

### Examples

| Field        | Value                         | Hex    |
| ------------ | ----------------------------- | ------ |
| command id   | `49`                          | `0x31` |
| command size | `3`                           | `0x03` |
| year         | `24` (`2000` + `24` = `2024`) | `0x18` |
| month        | `2` (February)                | `0x02` |
| date         | `19`                          | `0x13` |

Command hex dump: `31 03 18 02 13`


## Response

### Format

| Size | Type                          | Field                                                      |
| ---- | ----------------------------- | ---------------------------------------------------------- |
| `1`  | `uint8`                       | command id = `0x31`                                        |
| `1`  | `uint8`                       | command size = `27`                                        |
| `1`  | `uint8`                       | year (number of years after `2000`)                        |
| `1`  | `uint8`                       | month (`1` - January ... `12` - December)                  |
| `1`  | `uint8`                       | date (month day number which starts from `1`)              |
| `4`  | [tariffEnergy](#tariffenergy) | field set with time and energy for each tariff (`T1`-`T4`) |

#### tariffEnergy

Each power field is linked with the previous `hour` and `minutes` fields.

| Size | Type     | Field                                  |
| ---- | -------- | -------------------------------------- |
| `1`  | `uint8`  | hour                                   |
| `1`  | `uint8`  | minutes                                |
| `1`  | `uint32` | maximum power `P+` (`1.6.x`, x=`1..4`) |

### Examples

| Field              | Value                         | Hex          |
| ------------------ | ----------------------------- | ------------ |
| command id         | `49`                          | `0x31`       |
| command size       | `27`                          | `0x1b`       |
| year               | `24` (`2000` + `24` = `2024`) | `0x18`       |
| month              | `2` (February)                | `0x02`       |
| date               | `19`                          | `0x13`       |
| hour (`T1` start)  | `1`                           | `0x01`       |
| minutes            | `0`                           | `0x00`       |
| maximum power `P+` | `456`                         | `0x000001c8` |
| hour (`T2` start)  | `3`                           | `0x03`       |
| minutes            | `12`                          | `0x0c`       |
| maximum power `P+` | `9474`                        | `0x00002502` |
| hour (`T3` start)  | `7`                           | `0x07`       |
| minutes            | `30`                          | `0x1e`       |
| maximum power `P+` | `78573`                       | `0x000132ed` |
| hour (`T4` start)  | `12`                          | `0x0c`       |
| minutes            | `59`                          | `0x3b`       |
| maximum power `P+` | `395639`                      | `0x00060977` |

Command hex dump: `31 1b 18 02 13 01 00 000001c8 03 0c 00002502 07 1e 000132ed 0c 3b 00060977`


## See also

* [Access level](../basics.md#command-access-level)
