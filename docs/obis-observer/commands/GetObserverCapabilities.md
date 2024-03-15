# GetObserverCapabilities

Request/response the information about observer, like name, software and hardware version.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x03`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `3`   | `0x03` |
| command size | `1`   | `0x01` |
| request id   | `3`   | `0x03` |

Message hex dump: `03 01 03`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x04`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | `uint8`                              | max meter profiles number          |
| `1`  | `uint8`                              | max meter number                   |
| `1`  | `uint8`                              | max OBIS profiles number           |
| `1`  | `uint8`                              | is multi-mode supported            |


### Examples

| Field                     | Value | Hex    |
| ------------------------- | ----- | ------ |
| command id                | `04`  | `0x04` |
| command size              | `5`   | `0x05` |
| request id                | `7`   | `0x07` |
| max meter profiles number | `8`   | `0x08` |
| max meter number          | `8`   | `0x08` |
| max OBIS profiles number  | `8`   | `0x08` |
| is multi-mode supported   | `1`   | `0x01` |

Message hex dump: `04 05 07 08 08 08 01`


## See also

* [Request ID](../types.md#request-id)
* [Single mode](../single-mode.md)
