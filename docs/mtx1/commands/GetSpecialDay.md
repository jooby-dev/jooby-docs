# GetSpecialDay

Request/response to get special day information for the given tariff table.

The command access level is [READ_ONLY](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field                                                                                                                                                |
| ---- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x3d`                                                                                                                                  |
| `1`  | `uint8` | command size = `3`                                                                                                                                   |
| `1`  | `uint8` | tariff table identifier <br/> `0` – table `A+`, `1` – table `A-` (for `MTX1`)</br> `0` – table `A+`, `1` – table `P+`, `2` – table `A-` (for `MTX3`) |
| `1`  | `uint8` | special day index in a list of all tariff special days (max `26`)                                                                                    |
| `1`  | `uint8` | is it active or passive table (`0` - active, `1` - passive)                                                                                          |

### Examples

| Field        | Value   | Hex    |
| ------------ | ------- | ------ |
| command id   | `61`    | `0x3d` |
| command size | `3`     | `0x03` |
| tariff table | `A+`    | `0x00` |
| index        | `4`     | `0x04` |
| is active    | `false` | `0x01` |

Message hex dump: `3d 03 00 04 01`


## Response

### Format

| Size | Type    | Field                                           |
| ---- | ------- | ----------------------------------------------- |
| `1`  | `uint8` | command id = `0x3d`                             |
| `1`  | `uint8` | command size = `4`                              |
| `1`  | `uint8` | month                                           |
| `1`  | `uint8` | date                                            |
| `1`  | `uint8` | day profile index                               |
| `1`  | `uint8` | is it periodic or not (`0` - true, `1` - false) |

### Examples

| Field        | Value  | Hex    |
| ------------ | ------ | ------ |
| command id   | `61`   | `0x3d` |
| command size | `4`    | `0x04` |
| month        | `1`    | `0x01` |
| date         | `9`    | `0x09` |
| day index    | `3`    | `0x03` |
| is periodic  | `true` | `0x00` |

Message hex dump: `3d 04 01 09 03 00`


## See also

* [Access level](../basics.md#command-access-level)
