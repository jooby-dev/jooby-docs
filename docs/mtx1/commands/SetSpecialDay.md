# SetSpecialDay

Request/response to set special day information for the given tariff table.

The command access level is [READ_WRITE](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field                                                                                                                                                |
| ---- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x12`                                                                                                                                  |
| `1`  | `uint8` | command size = `6`                                                                                                                                   |
| `1`  | `uint8` | tariff table identifier <br/> `0` – table `A+`, `1` – table `A-` (for `MTX1`)</br> `0` – table `A+`, `1` – table `P+`, `2` – table `A-` (for `MTX3`) |
| `1`  | `uint8` | special day index in a list of all tariff special days (max `26`)                                                                                    |
| `1`  | `uint8` | month (`1` - January ... `12` - December)                                                                                                            |
| `1`  | `uint8` | date (month day number which starts from `1`)                                                                                                        |
| `1`  | `uint8` | day profile index                                                                                                                                    |
| `1`  | `uint8` | year (number of years after 2000). If year is equal to 0, the date is treated as periodic (month and day are fixed)                                  |

### Examples

| Field        | Value         | Hex    |
| ------------ | ------------- | ------ |
| command id   | `18`          | `0x12` |
| command size | `6`           | `0x06` |
| tariff table | `A-`          | `0x01` |
| index        | `5`           | `0x05` |
| month        | `1` (January) | `0x01` |
| date         | `9`           | `0x09` |
| day index    | `3`           | `0x03` |
| year         | `6`           | `0x06` |

Command hex dump: `12 06 01 05 01 09 03 06`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x12` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `18`  | `0x12` |
| command size | `0`   | `0x00` |

Command hex dump: `12 00`


## See also

* [Access level](../basics.md#command-access-level)
