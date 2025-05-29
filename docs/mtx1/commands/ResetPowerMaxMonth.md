# ResetPowerMaxMonth

Request/response for monthly max power reset

The command access level is [READ_WRITE](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x36` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `54`  | `0x36` |
| command size | `0`   | `0x00` |

Command hex dump: `36 00`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x36` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `54`  | `0x36` |
| command size | `0`   | `0x00` |

Command hex dump: `36 00`


## See also

* [Access level](../basics.md#command-access-level)
