# GetDisplayParam

Request/response to get the meter displays sorting order.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                       |
| ---- | ------- | ------------------------------------------- |
| `1`  | `uint8` | command id = `0x5e`                         |
| `1`  | `uint8` | command size = `1`                          |
| `1`  | `uint8` | display mode (`0` - main, `1` - additional) |

### Examples

| Field        | Value            | Hex    |
| ------------ | ---------------- | ------ |
| command id   | `94`             | `0x5e` |
| command size | `1`              | `0x01` |
| display mode | additional (`1`) | `0x01` |

Command hex dump: `5e 01 01`


## Response

### Format

| Size | Type    | Field                                                    |
| ---- | ------- | -------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x5e`                                      |
| `1`  | `uint8` | command size (dynamic, `1+`, max is `33`)                |
| `1`  | `uint8` | display mode (`0` - main, `1` - additional)              |
| `1+` | `uint8` | array of [display numbers](../basics.md#displays) to set |

### Examples

| Field        | Value                                                                                          | Hex          |
| ------------ | ---------------------------------------------------------------------------------------------- | ------------ |
| command id   | `94`                                                                                           | `0x5e`       |
| command size | `5`                                                                                            | `0x05`       |
| display mode | additional (`1`)                                                                               | `0x01`       |
| displays     | `TOTAL_ACTIVE_ENERGY` <br/> `CURRENT_IN_PHASE` <br/> `SOFTWARE_VERSION` <br/> `OPTOPORT_SPEED` | `0x030a021f` |

Command hex dump: `5e 05 01 03 0a 02 1f`


## See also

* [Access level](../basics.md#command-access-level)
* [Displays](../basics.md#displays)
