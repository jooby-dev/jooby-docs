# SetOpParamsExt3

Request/response to set device operator parameters `3`.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type     | Field                                                              |
| ---- | -------- | ------------------------------------------------------------------ |
| `1`  | `uint8`  | command id = `0x72`                                                |
| `1`  | `uint8`  | command size = `17`                                                |
| `4`  | `uint32` | Maximum threshold for negative active power for tariff `T1`, Watts |
| `4`  | `uint32` | Maximum threshold for negative active power for tariff `T2`, Watts |
| `4`  | `uint32` | Maximum threshold for negative active power for tariff `T3`, Watts |
| `4`  | `uint32` | Maximum threshold for negative active power for tariff `T4`, Watts |
| `1`  | `uint8`  | [Relay set](./GetOpParamsExt3.md#relay-set)                        |

### Examples

| Field                                                              | Value                                                                                                                                                                                                            | Hex          |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| command id                                                         | `114`                                                                                                                                                                                                            | `0x72`       |
| command size                                                       | `17`                                                                                                                                                                                                             | `0x11`       |
| Maximum threshold for negative active power for tariff `T1`, Watts | `100`                                                                                                                                                                                                            | `0x00000064` |
| Maximum threshold for negative active power for tariff `T2`, Watts | `200`                                                                                                                                                                                                            | `0x000000c8` |
| Maximum threshold for negative active power for tariff `T3`, Watts | `300`                                                                                                                                                                                                            | `0x0000012c` |
| Maximum threshold for negative active power for tariff `T4`, Watts | `400`                                                                                                                                                                                                            | `0x00000190` |
| [Relay set](./GetOpParamsExt3.md#relay-set)                        | `RELAY_OFF_NEGATIVE_ACTIVE_POWER_TARIFF_1`:`true`<br>`RELAY_OFF_NEGATIVE_ACTIVE_POWER_TARIFF_2`:`true`<br>`RELAY_OFF_NEGATIVE_ACTIVE_POWER_TARIFF_3`:`true`<br>`RELAY_OFF_NEGATIVE_ACTIVE_POWER_TARIFF_4`:`true` | `0x14`       |


Command hex dump: `72 11 00000064 000000c8 0000012c 00000190 14`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x72` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `114` | `0x72` |
| command size | `0`   | `0x00` |

Command hex dump: `72 00`


## See also

* [Access level](../basics.md#command-access-level)
