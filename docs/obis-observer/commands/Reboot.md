# Reboot

Request/response to restart the device.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x09`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `9`   | `0x09` |
| command size | `1`   | `0x01` |
| request id   | `3`   | `0x03` |

Message hex dump: `09 01 03`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x0a`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `10`  | `0x0a` |
| command size | `1`   | `0x01` |
| request id   | `3`   | `0x03` |

Message hex dump: `0a 01 03`

## See also

* [Request ID](../types.md#request-id)
