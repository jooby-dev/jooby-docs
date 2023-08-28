# GetSingleMode

Request to get the current mode (single or multi mode) of the observer device.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x0d`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `1`   | `0x0d` |
| command size | `1`   | `0x01` |
| request id   | `4`   | `0x04` |


Message hex dump: `0d 01 04`


## Response

### Format

| Size | Type                                 | Field                                           |
| ---- | ------------------------------------ | ----------------------------------------------- |
| `1`  | `byte`                               | command id = `0x0e`                             |
| `1`  | `byte`                               | command size                                    |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier              |
| `1`  | `byte`                               | Single mode: <br> `0` - multi <br> `1` - single |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `14`  | `0x0e` |
| command size | `2`   | `0x02` |
| request id   | `7`   | `0x07` |
| single mode  | `1`   | `0x01` |

Message hex dump: `0e 02 07 01`


## See also

* [Request ID](../types.md#request-id)
* [Single mode](../single-mode.md)
  