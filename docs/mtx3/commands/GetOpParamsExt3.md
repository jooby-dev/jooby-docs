# GetOpParamsExt3

Request/response to get device operator extended parameters `3`.

The command access level is [READ_ONLY](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x71` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `113` | `0x71` |
| command size | `0`   | `0x00` |

Message hex dump: `71 00`


## Response

### Format

| Size | Type     | Field                                                              |
| ---- | -------- | ------------------------------------------------------------------ |
| `1`  | `uint8`  | command id = `0x71`                                                |
| `1`  | `uint8`  | command size = `17`                                                |
| `4`  | `uint32` | Maximum threshold for negative active power for tariff `T1`, Watts |
| `4`  | `uint32` | Maximum threshold for negative active power for tariff `T2`, Watts |
| `4`  | `uint32` | Maximum threshold for negative active power for tariff `T3`, Watts |
| `4`  | `uint32` | Maximum threshold for negative active power for tariff `T4`, Watts |
| `1`  | `uint8`  | [Relay set](#relay-set)                                            |

### Parameters

#### Relay set

Bit mask:

| Name                                       | Bit | Description                                                      |
| ------------------------------------------ | --- | ---------------------------------------------------------------- |
| `RELAY_OFF_NEGATIVE_ACTIVE_POWER_TARIFF_1` | `3` | Disable by exceeding negative active power limit for tariff `T1` |
| `RELAY_OFF_NEGATIVE_ACTIVE_POWER_TARIFF_2` | `4` | Disable by exceeding negative active power limit for tariff `T2` |
| `RELAY_OFF_NEGATIVE_ACTIVE_POWER_TARIFF_3` | `5` | Disable by exceeding negative active power limit for tariff `T3` |
| `RELAY_OFF_NEGATIVE_ACTIVE_POWER_TARIFF_4` | `6` | Disable by exceeding negative active power limit for tariff `T4` |

### Examples

| Field                                                              | Value | Hex          |
| ------------------------------------------------------------------ | ----- | ------------ |
| command id                                                         | `113` | `0x71`       |
| command size                                                       | `17`  | `0x11`       |
| Maximum threshold for negative active power for tariff `T1`, Watts | `100` | `0x00000064` |
| Maximum threshold for negative active power for tariff `T2`, Watts | `200` | `0x000000c8` |
| Maximum threshold for negative active power for tariff `T3`, Watts | `300` | `0x0000012c` |
| Maximum threshold for negative active power for tariff `T4`, Watts | `400` | `0x00000190` |
| [Relay set](#relay-set)                                            | `?`   | `0x14`       |


Command hex dump: `71 11 00000064 000000c8 0000012c 00000190 14`


## See also

* [Access level](../basics.md#command-access-level)
