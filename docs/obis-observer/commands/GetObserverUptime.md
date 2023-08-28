# GetObserverUptime

Request/response the information about device uptime.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x03`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `3`   | `0x03` |
| command size | `1`   | `0x01` |
| request id   | `6`   | `0x06` |

Message hex dump: `03 01 06`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x04`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `4`  | `uint32_be`                          | uptime in seconds                  |


### Examples

| Field             | Value  | Hex          |
| ----------------- | ------ | ------------ |
| command id        | `4`    | `0x04`       |
| command size      | `5`    | `0x05`       |
| request id        | `6`    | `0x06`       |
| uptime in seconds | `4016` | `0x00000fb0` |

Message hex dump: `04 05 06 00 00 0f b0`


## See also

* [Request ID](../types.md#request-id)
