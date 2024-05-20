# UpdateImageVerify

Request/response to verify the update image on the device.
This command is part of update procedure.


## Request

### Format

| Size | Type                                 | Field                               |
| ---- | ------------------------------------ | ----------------------------------- |
| `1`  | `uint8`                              | command id = `0x32`                 |
| `1`  | `uint8`                              | command size                        |
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

| Size | Type                                 | Field                                                                  |
| ---- | ------------------------------------ | ---------------------------------------------------------------------- |
| `1`  | `uint8`                              | command id = `0x33`                                                    |
| `1`  | `uint8`                              | command size                                                           |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                     |
| `1`  | `uint8`                              | is image valid flag: <br/> `0` - invalid image <br/> `2` - valid image |


### Examples

#### success:

| Field               | Value | Hex    |
| ------------------- | ----- | ------ |
| command id          | `51`  | `0x33` |
| command size        | `2`   | `0x02` |
| request id          | `32`  | `0x20` |
| is image valid flag | `1`   | `0x01` |

Message hex dump: `33 02 20 01`

## See also

* [Request ID](../types.md#request-id)
