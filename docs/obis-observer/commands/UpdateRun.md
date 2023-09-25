# UpdateRun

Request/response to run the update on the device.
This command is part of update procedure.


## Request

### Format

| Size | Type                                 | Field                               |
| ---- | ------------------------------------ | ----------------------------------- |
| `1`  | `byte`                               | command id = `0x34`                 |
| `1`  | `byte`                               | command size                        |
| `1`  | [Request ID](../types.md#request-id) | request/response unique  identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `52`  | `0x34` |
| command size | `1`   | `0x01` |
| request id   | `33`  | `0x21` |

Message hex dump: `34 01 21`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x35`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples


| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `53`  | `0x35` |
| command size | `1`   | `0x01` |
| request id   | `32`  | `0x20` |

Message hex dump: `35 01 20`


## See also

* [Request ID](../types.md#request-id)
