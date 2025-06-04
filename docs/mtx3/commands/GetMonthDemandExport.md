# GetMonthDemandExport

Request/response to get the monthly energies (`A-`, `A-R+`, `A-R-`) for 4 tariffs (`T1`-`T4`).<br>
Applicable to type `G` meters.

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

| Size | Type    | Field                                                                   |
| ---- | ------- | ----------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x52`                                                     |
| `1`  | `uint8` | command size = `50`                                                     |
| `1`  | `uint8` | year (number of years after `2000`)                                     |
| `1`  | `uint8` | month (`1` - January ... `12` - December)                               |
| `4`  | `int32` | active energy for tariff `T1`, `A-` (`2.8.1`)                           |
| `4`  | `int32` | positive (inductive) reactive energy for tariff `T1`, `A-R+` (`6.8.1`)  |
| `4`  | `int32` | negative (capacitive) reactive energy for tariff `T1`, `A-R-` (`7.8.1`) |
| `4`  | `int32` | active energy for tariff `T2`, `A-` (`2.8.2`)                           |
| `4`  | `int32` | positive (inductive) reactive energy for tariff `T2`, `A-R+` (`6.8.2`)  |
| `4`  | `int32` | negative (capacitive) reactive energy for tariff `T2`, `A-R-` (`7.8.2`) |
| `4`  | `int32` | active energy for tariff `T3`, `A-` (`2.8.3`)                           |
| `4`  | `int32` | positive (inductive) reactive energy for tariff `T3`, `A-R+` (`6.8.3`)  |
| `4`  | `int32` | negative (capacitive) reactive energy for tariff `T3`, `A-R-` (`7.8.3`) |
| `4`  | `int32` | active energy for tariff `T4`, `A-` (`2.8.4`)                           |
| `4`  | `int32` | positive (inductive) reactive energy for tariff `T4`, `A-R+` (`6.8.4`)  |
| `4`  | `int32` | negative (capacitive) reactive energy for tariff `T4`, `A-R-` (`7.8.4`) |

### Examples

| Field                  | Value                         | Hex          |
| ---------------------- | ----------------------------- | ------------ |
| command id             | `82`                          | `0x52`       |
| command size           | `50`                          | `0x32`       |
| year                   | `24` (`2000` + `24` = `2024`) | `0x18`       |
| month                  | `3` (March)                   | `0x03`       |
| energy `A-` for `T1`   | `40301230`                    | `0x0266f2ae` |
| energy `A-R+` for `T1` | `25000`                       | `0x000061a8` |
| energy `A-R-` for `T1` | `987654`                      | `0x000f1206` |
| energy `A-` for `T2`   | `3334244`                     | `0x0032e064` |
| energy `A-R+` for `T2` | `1234567`                     | `0x0012d687` |
| energy `A-R-` for `T2` | `654321`                      | `0x0009fbf1` |
| energy `A-` for `T3`   | `15000`                       | `0x00003a98` |
| energy `A-R+` for `T3` | `789456`                      | `0x000c0bd0` |
| energy `A-R-` for `T3` | `123456`                      | `0x0001e240` |
| energy `A-` for `T4`   | `2145623`                     | `0x0020bd57` |
| energy `A-R+` for `T4` | `9876543`                     | `0x0096b43f` |
| energy `A-R-` for `T4` | `789012`                      | `0x000c0a14` |

Command hex dump:
```
52 32
18 03
0266f2ae 000061a8 000f1206
0032e064 0012d687 0009fbf1
00003a98 000c0bd0 0001e240
0020bd57 0096b43f 000c0a14
```


## See also

* [Access level](../basics.md#command-access-level)
