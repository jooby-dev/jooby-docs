# GetEnergy

Request/response to get current energies (`A+, R+, R-`) for all tariffs (`T1`-`T4`).

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

#### case #1 without energy type

| Size | Type    | Field                                         |
| ---- | ------- | --------------------------------------------- |
| `1`  | `uint8` | command id = `0x0f`                           |
| `1`  | `uint8` | command size = `0`                            |

### Examples

#### request the current energies

| Field        | Value       | Hex    |
| ------------ | ----------- | ------ |
| command id   | `15`        | `0x0f` |
| command size | `0`         | `0x00` |

Command hex dump: `0f 00`


## Response

### Format

| Size | Type    | Field                                                 |
| ---- | ------- | ----------------------------------------------------- |
| `1`  | `uint8` | command id = `0x0f`                                   |
| `1`  | `uint8` | command size = `48`                                   |
| `4`  | `int32` | active energy `A+` (`1.8.1`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A+R+` (`5.8.1`) |
| `4`  | `int32` | negative (capacitive) reactive `A+R-` (`8.8.1`)       |
| `4`  | `int32` | active energy `A+` (`1.8.2`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A+R+` (`5.8.2`) |
| `4`  | `int32` | negative (capacitive) reactive `A+R-` (`8.8.2`)       |
| `4`  | `int32` | active energy `A+` (`1.8.3`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A+R+` (`5.8.3`) |
| `4`  | `int32` | negative (capacitive) reactive `A+R-` (`8.8.3`)       |
| `4`  | `int32` | active energy `A+` (`1.8.4`)                          |
| `4`  | `int32` | positive (inductive) reactive energy `A+R+` (`5.8.4`) |
| `4`  | `int32` | negative (capacitive) reactive `A+R-` (`8.8.4`)       |


### Examples

| Field            | Value       | Hex        |
| ---------------- | ----------- | ---------- |
| command id       | `15`        | `0x0f`     |
| command size     | `48`        | `0x30`     |
| `A+` (`1.8.1`)   | `0266f2ae`  | `40301230` |
| `A+R+` (`5.8.1`) | `0032e064`  | `3334244`  |
| `A+R-` (`8.8.1`) | `0000091d`  | `2333`     |
| `A+` (`1.8.2`)   | `0020bd57`  | `2145623`  |
| `A+R+` (`5.8.2`) | `0020bd58`  | `2145624`  |
| `A+R-` (`8.8.2`) | `0020bd59`  | `2145625`  |
| `A+` (`1.8.3`)   | `0020bd5a`  | `2145626`  |
| `A+R+` (`5.8.3`) | `0020bd5b`  | `2145627`  |
| `A+R-` (`8.8.3`) | `0020bd5c`  | `2145628`  |
| `A+` (`1.8.4`)   | `0020bd5d`  | `2145629`  |
| `A+R+` (`5.8.4`) | `0020bd5e`  | `2145630`  |
| `A+R-` (`8.8.4`) | `0020bd5f`  | `2145631`  |

Command hex dump:
```
0f 30
0266f2ae 0032e064 0000091d
0020bd57 0020bd58 0020bd59
0020bd5a 0020bd5b 0020bd5c
0020bd5d 0020bd5e 0020bd5f
```

## See also

* [Access level](../basics.md#command-access-level)
