# GetMonthDemandExport

Request/response to get the monthly active energy (`A-`) for all tariffs (`T1`-`T4`).

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                     |
| ---- | ------- | ----------------------------------------- |
| `1`  | `uint8` | command id = `0x52`                       |
| `1`  | `uint8` | command size = `2`                        |
| `1`  | `uint8` | year (number of years after `2000`)       |
| `1`  | `uint8` | month (`1` - January ... `12` - December) |

### Examples

| Field        | Value                         | Hex    |
| ------------ | ----------------------------- | ------ |
| command id   | `82`                          | `0x52` |
| command size | `2`                           | `0x02` |
| year         | `24` (`2000` + `24` = `2024`) | `0x18` |
| month        | `3` (March)                   | `0x03` |

Command hex dump: `52 02 18 03`


## Response

### Format

| Size  | Type    | Field                                                        |
| ----- | ------- | ------------------------------------------------------------ |
| `1`   | `uint8` | command id = `0x52`                                          |
| `1`   | `uint8` | command size = `18`                                          |
| `1`   | `uint8` | year (number of years after `2000`)                          |
| `1`   | `uint8` | month (`1` - January ... `12` - December)                    |
| `4*n` | `int32` | active energy `A-` for tariffs `T1`-`T4` (`2.8.x`, x=`1..4`) |

> `n` - the number of tariffs.

### Examples

| Field           | Value                         | Hex          |
| --------------- | ----------------------------- | ------------ |
| command id      | `82`                          | `0x52`       |
| command size    | `18`                          | `0x12`       |
| year            | `24` (`2000` + `24` = `2024`) | `0x18`       |
| month           | `3` (March)                   | `0x03`       |
| energy for `T1` | `40301230`                    | `0x0266f2ae` |
| energy for `T2` | `3334244`                     | `0x0032e064` |
| energy for `T3` | `2333`                        | `0x0000091d` |
| energy for `T4` | `2145623`                     | `0x0020bd57` |

Command hex dump: `52 12 18 03 0266f2ae 0032e064 0000091d 0020bd57`


## See also

* [Access level](../basics.md#command-access-level)
