# RemoveMeter

Request/response to remove specific meter device.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x72`                |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | `byte`                               | command size                       |
| `1`  | [Meter ID](../types.md#meter-id)     | meter unique identifier            |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `114` | `0x72` |
| command size | `2`   | `0x02` |
| request id   | `121` | `0x29` |
| meter id     | `1`   | `0x01` |

Message hex dump: `72 02 29 01`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x73`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `115` | `0x73` |
| command size | `1`   | `0x01` |
| request id   | `156` | `0x9c` |

Message hex dump: `73 01 9c`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description                            |
| ----------- | -------------------------------------- |
| `3`         | Format error.                          |
| `11`        | The single-multi meter mode collision. |


## See alsos

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
