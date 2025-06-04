# GetEnergyDayExport

Request/response to get daily energies (`A-, R+, R-`) for all tariffs (`T1`-`T4`) for date.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                         |
| ---- | ------- | --------------------------------------------- |
| `1`  | `uint8` | command id = `0x4f`                           |
| `1`  | `uint8` | command size = `3`                            |
| `1`  | `uint8` | year (number of years after `2000`)           |
| `1`  | `uint8` | month (`1` - January ... `12` - December)     |
| `1`  | `uint8` | date (month day number which starts from `1`) |

### Examples

#### request the daily energies (`A-, R+, R-`) for 2024.03.22

| Field        | Value       | Hex    |
| ------------ | ----------- | ------ |
| command id   | `79`        | `0x4f` |
| command size | `3`         | `0x03` |
| year         | `24`        | `0x18` |
| month        | `3` (March) | `0x03` |
| date         | `22`        | `0x16` |

Command hex dump: `4f 03 18 03 16`


## Response

### Format

| Size | Type    | Field                                                 |
| ---- | ------- | ----------------------------------------------------- |
| `1`  | `uint8` | command id = `0x4f`                                   |
| `1`  | `uint8` | command size = `51`                                   |
| `1`  | `uint8` | year (number of years after `2000`)                   |
| `1`  | `uint8` | month (`1` - January ... `12` - December)             |
| `1`  | `uint8` | date (month day number which starts from `1`)         |
| `4`  | `int32` | active energy `A-` (`2.8.1`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A-R+` (`6.8.1`) |
| `4`  | `int32` | negative (capacitive) reactive `A-R-` (`7.8.1`)       |
| `4`  | `int32` | active energy `A-` (`2.8.2`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A-R+` (`6.8.2`) |
| `4`  | `int32` | negative (capacitive) reactive `A-R-` (`7.8.2`)       |
| `4`  | `int32` | active energy `A-` (`2.8.3`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A-R+` (`6.8.3`) |
| `4`  | `int32` | negative (capacitive) reactive `A-R-` (`7.8.3`)       |
| `4`  | `int32` | active energy `A-` (`2.8.4`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A-R+` (`6.8.4`) |
| `4`  | `int32` | negative (capacitive) reactive `A-R-` (`7.8.4`)       |


### Examples

| Field            | Value       | Hex        |
| ---------------- | ----------- | ---------- |
| command id       | `22`        | `0x16`     |
| command size     | `51`        | `0x33`     |
| year             | `24`        | `0x18`     |
| month            | `3` (March) | `0x03`     |
| date             | `22`        | `0x16`     |
| `A-` (`2.8.1`)   | `0266f2ae`  | `40301230` |
| `A-R+` (`6.8.1`) | `0032e064`  | `3334244`  |
| `A-R-` (`7.8.1`) | `0000091d`  | `2333`     |
| `A-` (`2.8.2`)   | `0020bd57`  | `2145623`  |
| `A-R+` (`6.8.2`) | `0020bd58`  | `2145624`  |
| `A-R-` (`7.8.2`) | `0020bd59`  | `2145625`  |
| `A-` (`2.8.3`)   | `0020bd5a`  | `2145626`  |
| `A-R+` (`6.8.3`) | `0020bd5b`  | `2145627`  |
| `A-R-` (`7.8.3`) | `0020bd5c`  | `2145628`  |
| `A-` (`2.8.4`)   | `0020bd5d`  | `2145629`  |
| `A-R+` (`6.8.4`) | `0020bd5e`  | `2145630`  |
| `A-R-` (`7.8.4`) | `0020bd5f`  | `2145631`  |

Command hex dump:
```
16 33
18 03 16
0266f2ae 0032e064 0000091d
0020bd57 0020bd58 0020bd59
0020bd5a 0020bd5b 0020bd5c
0020bd5d 0020bd5e 0020bd5f
```


## See also

* [Access level](../basics.md#command-access-level)
