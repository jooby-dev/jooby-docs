# GetSerialPort

Request/response the information about serial port settings.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x07`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `3`   | `0x07` |
| command size | `1`   | `0x01` |
| request id   | `6`   | `0x06` |

Message hex dump: `07 01 06`


## Response

### Format

| Size | Type                                 | Field                                |
| ---- | ------------------------------------ | ------------------------------------ |
| `1`  | `uint8`                              | command id = `0x08`                  |
| `1`  | `uint8`                              | command size                         |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier   |
| `1`  | [baud rate](../types.md#baud-rate)   | serial port baud rate                |
| `1`  | [data bits](../types.md#data-bits)   | serial port word length or data bits |
| `1`  | [parity](../types.md#parity)         | serial port parity settings          |

### Examples

| Field        | Value  | Hex    |
| ------------ | ------ | ------ |
| command id   | `8`    | `0x08` |
| command size | `4`    | `0x04` |
| request id   | `52`   | `0x34` |
| baud rate    | `9600` | `0x05` |
| data bits    | `8`    | `0x08` |
| parity       | `odd`  | `0x01` |

Message hex dump: `08 04 34 05 08 01`


## See also

* [Request ID](../types.md#request-id)
* [baud rate](../types.md#baud-rate)
* [data bits](../types.md#data-bits)
* [parity](../types.md#parity)
