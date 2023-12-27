# Reboot

Request/response to restart the device.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x26`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `38`  | `0x26` |
| command size | `1`   | `0x01` |
| request id   | `3`   | `0x03` |

Message hex dump: `26 01 03`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x27`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `39`  | `0x27` |
| command size | `1`   | `0x01` |
| request id   | `3`   | `0x03` |

Message hex dump: `27 01 03`

## See also

* [Request ID](../types.md#request-id)
