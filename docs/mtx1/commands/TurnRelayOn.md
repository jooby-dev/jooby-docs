# TurnRelayOn

Request/response to turn the device relay on.

The command access level is [READ_WRITE](../basics.md#command-access-level).

Supported devices:
- MTX1
- MTX3


## Request

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x18` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `24`  | `0x18` |
| command size | `0`   | `0x00` |

Message hex dump: `18 00`


## Response

### Format

| Size | Type    | Field               |
| ---- | ------- | ------------------- |
| `1`  | `uint8` | command id = `0x18` |
| `1`  | `uint8` | command size = `0`  |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `24`  | `0x18` |
| command size | `0`   | `0x00` |

Message hex dump: `18 00`


## See also

* [Access level](../basics.md#command-access-level)
