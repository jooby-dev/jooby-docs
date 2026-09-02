# ResetSettings

Request/response to reset observer device settings.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x92`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `146` | `0x92` |
| command size | `1`   | `0x01` |
| request id   | `3`   | `0x03` |

Message hex dump: `92 01 03`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x93`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `147` | `0x93` |
| command size | `1`   | `0x01` |
| request id   | `7`   | `0x07` |

Message hex dump: `93 01 07`


## See also

* [Request ID](../types.md#request-id)
