# UpdateImageVerify

Request/response to verify the update image on the device.
This command is part of update procedure.


## Request

### Format

| Size | Type                                 | Field                               |
| ---- | ------------------------------------ | ----------------------------------- |
| `1`  | `byte`                               | command id = `0x2c`                 |
| `1`  | [Request ID](../types.md#request-id) | request/response unique  identifier |


### Examples

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `44`  | `0x2c` |
| request id | `33`  | `0x21` |

Message hex dump: `2c 21`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x2d`                |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |


### Examples

#### success:

| Field       | Value | Hex    |
| ----------- | ----- | ------ |
| command id  | `43`  | `0x2d` |
| request id  | `32`  | `0x20` |
| result code | `OK`  | `0x00` |

Message hex dump: `2b 20 00`

#### failure:

| Field       | Value     | Hex    |
| ----------- | --------- | ------ |
| command id  | `43`      | `0x2d` |
| request id  | `32`      | `0x20` |
| result code | `FAILURE` | `0x01` |

Message hex dump: `2d 20 01`


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
