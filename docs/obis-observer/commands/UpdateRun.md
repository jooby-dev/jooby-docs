# UpdateRun

Request/response to run the update on the device.
This command is part of update procedure.


## Request

### Format

| Size | Type                                 | Field                               |
| ---- | ------------------------------------ | ----------------------------------- |
| `1`  | `byte`                               | command id = `0x2e`                 |
| `1`  | [Request ID](../types.md#request-id) | request/response unique  identifier |


### Examples

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `46`  | `0x2e` |
| request id | `33`  | `0x21` |

Message hex dump: `2e 21`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x2f`                |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |


### Examples

#### success:

| Field       | Value | Hex    |
| ----------- | ----- | ------ |
| command id  | `47`  | `0x2f` |
| request id  | `32`  | `0x20` |
| result code | `OK`  | `0x00` |

Message hex dump: `2f 20 00`

#### failure:

| Field       | Value     | Hex    |
| ----------- | --------- | ------ |
| command id  | `47`      | `0x1f` |
| request id  | `32`      | `0x20` |
| result code | `FAILURE` | `0x01` |

Message hex dump: `2f 20 01`


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
