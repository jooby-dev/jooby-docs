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

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x73`                |
| `1`  | `byte`                                 | command size                       |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `115` | `0x73` |
| command size | `2`   | `0x02` |
| request id   | `156` | `0x9c` |
| result code  | `0`   | `0x00` |

Message hex dump: `73 02 9c 00`

#### the meter not found

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `115` | `0x73` |
| command size | `2`   | `0x02` |
| request id   | `49`  | `0x31` |
| result code  | `1 `  | `0x07` |

Message hex dump: `73 02 31 07`


### Result codes:

| Result code | Description                       |
| ----------- | --------------------------------- |
| `0`         | Ok. The Operation was successful. |
| `7`         | The meter not found.              |


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
* [Meter ID](../types.md#meter-id)
