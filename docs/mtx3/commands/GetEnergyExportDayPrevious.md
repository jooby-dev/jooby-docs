# GetEnergyExportDayPrevious

Request/response to get previous daily energy (`A-, R+, R-`) for all tariffs (`T1`-`T4`).
Applicable to type `G` meters.


The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x50` |
| `1`  | `uint8` | command size = `0`  |

### Examples

#### request the previous day energy (`A+, R+, R-`)

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `80`  | `0x50` |
| command size | `0`   | `0x00` |

Command hex dump: `50 00`

## Response

### Format

#### response to request without energy type

| Size | Type    | Field                                                                   |
| ---- | ------- | ----------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x16`                                                     |
| `1`  | `uint8` | command size = `51`                                                     |
| `1`  | `uint8` | year (number of years after `2000`)                                     |
| `1`  | `uint8` | month (`1` - January ... `12` - December)                               |
| `1`  | `uint8` | date (month day number which starts from `1`)                           |
| `4`  | `int32` | active energy for tariff `T1`, `A-` (`2.8.1`)                           |
| `4`  | `int32` | positive (inductive) reactive energy for tariff `T1`, `A-R+` (`6.8.1`)  |
| `4`  | `int32` | negative (capacitive) reactive energy for tariff `T1`, `A-R-` (`7.8.1`) |
| `4`  | `int32` | active energy for tariff `T2`, `A-` (`2.8.2`)                           |
| `4`  | `int32` | positive (inductive) reactive energy for tariff `T2`, `A-R+` (`6.8.2`)  |
| `4`  | `int32` | negative (capacitive) reactive for tariff `T2`, `A-R-` (`7.8.2`)        |
| `4`  | `int32` | active energy for tariff `T3`, `A-` (`2.8.3`)                           |
| `4`  | `int32` | positive (inductive) reactive energy for tariff `T3`, `A-R+` (`6.8.3`)  |
| `4`  | `int32` | negative (capacitive) reactive energy for tariff `T3`, `A-R-` (`7.8.3`) |
| `4`  | `int32` | active energy for tariff `T4`, `A-` (`2.8.4`)                           |
| `4`  | `int32` | positive (inductive) reactive energy for tariff `T4`, `A-R+` (`6.8.4`)  |
| `4`  | `int32` | negative (capacitive) reactive energy for tariff `T4`, `A-R-` (`7.8.4`) |

### Examples

| Field            | Value       | Hex          |
| ---------------- | ----------- | ------------ |
| command id       | `80`        | `0x50`       |
| command size     | `51`        | `0x33`       |
| year             | `24`        | `0x18`       |
| month            | `3` (March) | `0x03`       |
| date             | `22`        | `0x16`       |
| `A-` (`2.8.1`)   | `40301230`  | `0x0266f2ae` |
| `A-R+` (`6.8.1`) | `3334244`   | `0x0032e064` |
| `A-R-` (`7.8.1`) | `2333`      | `0x0000091d` |
| `A-` (`2.8.2`)   | `2145623`   | `0x0020bd57` |
| `A-R+` (`7.8.2`) | `2145624`   | `0x0020bd58` |
| `A-R-` (`4.8.2`) | `2145625`   | `0x0020bd59` |
| `A-` (`2.8.3`)   | `2145626`   | `0x0020bd5a` |
| `A-R+` (`6.8.3`) | `2145627`   | `0x0020bd5b` |
| `A-R-` (`7.8.3`) | `2145628`   | `0x0020bd5c` |
| `A-` (`2.8.4`)   | `2145629`   | `0x0020bd5d` |
| `A-R+` (`6.8.4`) | `2145630`   | `0x0020bd5e` |
| `A-R-` (`7.8.4`) | `2145631`   | `0x0020bd5f` |

Command hex dump:
```
50 33
18 03 16
0266f2ae 0032e064 0000091d
0020bd57 0020bd58 0020bd59
0020bd5a 0020bd5b 0020bd5c
0020bd5d 0020bd5e 0020bd5f
```


## See also

* [Access level](../basics.md#command-access-level)
