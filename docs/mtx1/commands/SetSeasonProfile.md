# SetSeasonProfile

Request/response to set season profile information for the given tariff table.

The command access level is [READ_WRITE](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field                                                                                                                                                |
| ---- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x11`                                                                                                                                  |
| `1`  | `uint8` | command size = `11`                                                                                                                                  |
| `1`  | `uint8` | tariff table identifier <br/> `0` – table `A+`, `1` – table `A-` (for `MTX1`)</br> `0` – table `A+`, `1` – table `P+`, `2` – table `A-` (for `MTX3`) |
| `1`  | `uint8` | season profile index in a list of all tariff seasons (max `14`)                                                                                      |
| `1`  | `uint8` | month (`1` - January ... `12` - December)                                                                                                            |
| `1`  | `uint8` | date (month day number which starts from `1`)                                                                                                        |
| `7`  | `uint8` | day profile indexes for a week                                                                                                                       |

### Examples

| Field                  | Value         | Hex    |
| ---------------------- | ------------- | ------ |
| command id             | `17`          | `0x11` |
| command size           | `11`          | `0x0b` |
| tariff table           | `A+`          | `0x00` |
| index                  | `4`           | `0x04` |
| month                  | `1` (January) | `0x01` |
| date                   | `9`           | `0x09` |
| day profile index `#0` | `0`           | `0x00` |
| day profile index `#1` | `1`           | `0x01` |
| day profile index `#2` | `0`           | `0x00` |
| day profile index `#3` | `1`           | `0x01` |
| day profile index `#4` | `0`           | `0x00` |
| day profile index `#5` | `1`           | `0x01` |
| day profile index `#6` | `0`           | `0x00` |

Command hex dump: `11 0b 00 04 01 09 00 01 00 01 00 01 00`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x11` |
| `1`  | `uint8` | command size = `0`  |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `17`  | `0x11` |
| command size | `0`   | `0x00` |

Command hex dump: `11 00`


## See also

* [Access level](../basics.md#command-access-level)
