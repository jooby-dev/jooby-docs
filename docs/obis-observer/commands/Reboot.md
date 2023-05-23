# Reboot

Request/response to restart the device.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x1c`                |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |

### Examples

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `5`   | `0x1c` |
| request id | `3`   | `0x03` |

Message hex dump: `1c 03`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x1d`                |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |

### Examples

#### success:

| Field       | Value | Hex    |
| ----------- | ----- | ------ |
| command id  | `6`   | `0x1d` |
| request id  | `3`   | `0x03` |

Message hex dump: `1d 03`


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
