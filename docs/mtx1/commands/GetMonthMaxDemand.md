# GetMonthMaxDemand

Request/response to get the maximum monthly power `P+` for all tariffs (`T1`-`T4`).

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                     |
| ---- | ------- | ----------------------------------------- |
| `1`  | `uint8` | command id = `0x32`                       |
| `1`  | `uint8` | command size = `2`                        |
| `1`  | `uint8` | year (number of years after `2000`)       |
| `1`  | `uint8` | month (`1` - January ... `12` - December) |

### Examples

| Field        | Value                         | Hex    |
| ------------ | ----------------------------- | ------ |
| command id   | `50`                          | `0x32` |
| command size | `2`                           | `0x02` |
| year         | `24` (`2000` + `24` = `2024`) | `0x18` |
| month        | `3` (March)                   | `0x03` |

Command hex dump: `32 02 18 03`


## Response

### Format

| Size  | Type                          | Field                                                      |
| ----- | ----------------------------- | ---------------------------------------------------------- |
| `1`   | `uint8`                       | command id = `0x32`                                        |
| `1`   | `uint8`                       | command size = `30`                                        |
| `1`   | `uint8`                       | year (number of years after `2000`)                        |
| `1`   | `uint8`                       | month (`1` - January ... `12` - December)                  |
| `7*n` | [tariffEnergy](#tariffenergy) | field set with time and energy for each tariff (`T1`-`T4`) |

> `n` - the number of tariffs.

#### tariffEnergy

Each power field is linked with the previous `date`, `hour` and `minutes` fields.

| Size | Type     | Field                                         |
| ---- | -------- | --------------------------------------------- |
| `1`  | `uint8`  | date (month day number which starts from `1`) |
| `1`  | `uint8`  | hour                                          |
| `1`  | `uint8`  | minutes                                       |
| `4`  | `uint32` | maximum power `P+` (`1.6.x`, x=`1..4`)        |

### Examples

| Field              | Value                         | Hex          |
| ------------------ | ----------------------------- | ------------ |
| command id         | `50`                          | `0x32`       |
| command size       | `30`                          | `0x1e`       |
| year               | `24` (`2000` + `24` = `2024`) | `0x18`       |
| month              | `3` (March)                   | `0x03`       |
| date (`T1` start)  | `22`                          | `0x16`       |
| hour               | `12`                          | `0x0c`       |
| minutes            | `48`                          | `0x30`       |
| maximum power `P+` | `2424`                        | `0x00000978` |
| date (`T2` start)  | `12`                          | `0x0c`       |
| hour               | `12`                          | `0x0c`       |
| minutes            | `33`                          | `0x21`       |
| maximum power `P+` | `3644`                        | `0x00000e3c` |
| date (`T3` start)  | `25`                          | `0x19`       |
| hour               | `15`                          | `0x0f`       |
| minutes            | `4`                           | `0x04`       |
| maximum power `P+` | `1244`                        | `0x000004dc` |
| date (`T4` start)  | `8`                           | `0x08`       |
| hour               | `17`                          | `0x11`       |
| minutes            | `32`                          | `0x20`       |
| maximum power `P+` | `5244`                        | `0x0000147c` |

Command hex dump:
```
32 1e
18 03
16 0c 30 00000978
0c 0c 21 00000e3c
19 0f 04 000004dc
08 11 20 0000147c
```

## See also

* [Access level](../basics.md#command-access-level)
