# GetObserverUptime

Request/response the information about device uptime.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x05`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `5`   | `0x05` |
| command size | `1`   | `0x01` |
| request id   | `6`   | `0x06` |

Message hex dump: `05 01 06`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x06`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `4`  | `uint32_be`                          | uptime in seconds                  |


### Examples

| Field             | Value  | Hex          |
| ----------------- | ------ | ------------ |
| command id        | `6`    | `0x06`       |
| command size      | `5`    | `0x05`       |
| request id        | `6`    | `0x06`       |
| uptime in seconds | `4016` | `0x00000fb0` |

Message hex dump: `06 05 06 00 00 0f b0`


## See also

* [Request ID](../types.md#request-id)
