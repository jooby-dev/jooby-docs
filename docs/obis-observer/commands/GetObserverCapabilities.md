# GetObserverCapabilities

Request/response the information about observer, like name, software and hardware version.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x19`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `25`  | `0x19` |
| command size | `1`   | `0x01` |
| request id   | `3`   | `0x03` |

Message hex dump: `19 01 03`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x1a`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | `byte`                               | max meter profiles number          |
| `1`  | `byte`                               | max meter number                   |
| `1`  | `byte`                               | max OBIS profiles number           |
| `1`  | `byte`                               | is multi-mode supported            |


### Examples

| Field                     | Value | Hex    |
| ------------------------- | ----- | ------ |
| command id                | `26`  | `0x1a` |
| command size              | `5`   | `0x05` |
| request id                | `7`   | `0x07` |
| max meter profiles number | `8`   | `0x08` |
| max meter number          | `8`   | `0x08` |
| max OBIS profiles number  | `8`   | `0x08` |
| is multi-mode supported   | `1`   | `0x01` |

Message hex dump: `1a 05 08 08 08 01`


## See also

* [Request ID](../types.md#request-id)
* [Single mode](../single-mode.md)
