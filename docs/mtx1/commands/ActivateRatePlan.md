# ActivateRatePlan

Request/response to provide the date and parameters of tariff plan activation.

The command access level is [READ_WRITE](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type     | Field                                                                                                                                                |
| ---- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8`  | command id = `0x13`                                                                                                                                  |
| `1`  | `uint8`  | command size = `12`                                                                                                                                  |
| `1`  | `uint8`  | tariff table identifier <br/> `0` – table `A+`, `1` – table `A-` (for `MTX1`)</br> `0` – table `A+`, `1` – table `P+`, `2` – table `A-` (for `MTX3`) |
| `4`  | `uint32` | rate plan unique identifier                                                                                                                          |
| `1`  | `uint8`  | indicates the state of this tariff plan (`1` - tariff table is valid, `0` - not valid)                                                               |
| `1`  | `uint8`  | activation year (number of years after `2000`)                                                                                                       |
| `1`  | `uint8`  | activation month (`1` - January ... `12` - December)                                                                                                 |
| `1`  | `uint8`  | activation date (month day number which starts from `1`)                                                                                             |
| `1`  | `uint8`  | the number of special days in the tariff table (max `26`)                                                                                            |
| `1`  | `uint8`  | the number of seasons in the tariff table (max `14`)                                                                                                 |
| `1`  | `uint8`  | the number of days in the tariff table (max `32`)                                                                                                    |


### Examples

Activate `A+` table for plan id `1` at `2024.02.19`:

| Field           | Value                         | Hex          |
| --------------- | ----------------------------- | ------------ |
| command id      | `19`                          | `0x13`       |
| command size    | `12`                          | `0x0c`       |
| tariff table    | `A+`                          | `0x00`       |
| rate plan id    | `1`                           | `0x00000001` |
| tariff state    | `valid`                       | `0x01`       |
| year            | `24` (`2000` + `24` = `2024`) | `0x18`       |
| month           | `2` (February)                | `0x02`       |
| date            | `19`                          | `0x13`       |
| special days    | `6`                           | `0x06`       |
| season profiles | `7`                           | `0x07`       |
| day profiles    | `8`                           | `0x08`       |

Command hex dump: `13 0c 00 00 00 00 01 01 18 02 13 06 07 08`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x13` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `19`  | `0x13` |
| command size | `0`   | `0x00` |

Command hex dump: `13 00`


## See also

* [Access level](../basics.md#command-access-level)
