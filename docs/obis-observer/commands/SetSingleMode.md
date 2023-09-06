# SetSingleMode

Request to set the single or multi mode of the observer device.


## Request

### Format

| Size | Type                                 | Field                                           |
| ---- | ------------------------------------ | ----------------------------------------------- |
| `1`  | `byte`                               | command id = `0x0b`                             |
| `1`  | `byte`                               | command size                                    |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier              |
| `1`  | `byte`                               | Single mode: <br> `0` - multi <br> `1` - single |


### Examples

#### get profile for OBIS ID `128`:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `1`   | `0x0b` |
| command size | `2`   | `0x02` |
| request id   | `4`   | `0x04` |
| single mode  | `1`   | `0x01` |

Message hex dump: `0b 02 04 01`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x0c`                |
| `1`  | `byte`                                 | command size                       |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `12`  | `0x0c` |
| command size | `2`   | `0x02` |
| request id   | `156` | `0x9c` |
| result code  | `0`   | `0x00` |

Message hex dump: `0c 02 9c 00`

#### the multi mode unsupported:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `12`  | `0x0c` |
| command size | `2`   | `0x02` |
| request id   | `156` | `0x9c` |
| result code  | `12`  | `0x0c` |

Message hex dump: `0c 02 9c 0c`


### Result codes:

| Result code | Description                       |
| ----------- | --------------------------------- |
| `0`         | Ok. The Operation was successful. |
| `12`        | The multi meter mode unsupported. |


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
* [Single mode](../single-mode.md)
