# GetArchiveProfile

Request/response to get the archive info.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x0d`                |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |

### Examples

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `1`   | `0x0d` |
| request id | `3`   | `0x03` |

Message hex dump: `0d 03`


## Response

### Format

| Size | Type                                 | Field                                                                  |
| ---- | ------------------------------------ | ---------------------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x0e`                                                    |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                     |
| `2`  | `uint16_be`                          | archive period for the `Summary Archive` in minutes (default: `24*60`) |
| `2`  | `uint16_be`                          | archive period for the `Detailed Archive` in minutes (default: `15`)   |

### Examples

#### default periods:

| Field                   | Value | Hex      |
| ----------------------- | ----- | -------- |
| command id              | `14`  | `0x0e`   |
| request id              | `3`   | `0x03`   |
| summary archive period  | `600` | `0x0258` |
| detailed archive period | `45`  | `0x002d` |


Message hex dump: `0e 03 02 58 00 2d`


## See also

* [Request ID](../types.md#request-id)
