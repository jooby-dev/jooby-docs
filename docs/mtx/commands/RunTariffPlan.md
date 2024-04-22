# RunTariffPlan

Request/response for instant activation of the passive tariff plan.

The command access level is [READ_WRITE](../basics.md#command-access-level).


## Request

### Format

| Size | Type    | Field                                                             |
| ---- | ------- | ----------------------------------------------------------------- |
| `1`  | `uint8` | command id = `0x06`                                               |
| `1`  | `uint8` | command size = `1`                                                |
| `1`  | `uint8` | tariff table identifier<br/> (`0` - table `A+`, `1` – table `A-`) |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `6`   | `0x06` |
| command size | `1`   | `0x01` |
| tariff table | `A+`  | `0x00` |

Message hex dump: `06 01 00`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x06` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `6`   | `0x06` |
| command size | `0`   | `0x00` |

Message hex dump: `06 00`


## See also

* [Access level](../basics.md#command-access-level)
