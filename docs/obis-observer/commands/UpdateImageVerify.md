# UpdateImageVerify

Request/response to verify the update image on the device.
This command is part of update procedure.


## Request

### Format

| Size | Type                                 | Field                               |
| ---- | ------------------------------------ | ----------------------------------- |
| `1`  | `byte`                               | command id = `0x32`                 |
| `1`  | `byte`                               | command size                        |
| `1`  | [Request ID](../types.md#request-id) | request/response unique  identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `50`  | `0x32` |
| command size | `1`   | `0x01` |
| request id   | `33`  | `0x21` |

Message hex dump: `32 01 21`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x33`                |
| `1`  | `byte`                                 | command size                       |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `51`  | `0x33` |
| command size | `2`   | `0x02` |
| request id   | `32`  | `0x20` |
| result code  | `0`   | `0x00` |

Message hex dump: `33 02 20 00`

#### failure:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `51`  | `0x33` |
| command size | `2`   | `0x02` |
| request id   | `32`  | `0x20` |
| result code  | `1`   | `0x01` |

Message hex dump: `33 02 20 01`


### Result codes:

| Result code | Description                       |
| ----------- | --------------------------------- |
| `0`         | Ok. The Operation was successful. |
| `1`         | General failure. Invalid crc.     |


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
