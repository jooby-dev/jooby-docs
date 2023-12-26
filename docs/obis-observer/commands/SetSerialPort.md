# SetSerialPort

Request/response to set serial port parameters.


## Request

### Format

| Size | Type                                 | Field                                |
| ---- | ------------------------------------ | ------------------------------------ |
| `1`  | `byte`                               | command id = `0x09`                  |
| `1`  | `byte`                               | command size                         |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier   |
| `1`  | [baud rate](../types.md#baud-rate)   | serial port baud rate                |
| `1`  | [data bits](../types.md#data-bits)   | serial port word length or data bits |
| `1`  | [parity](../types.md#parity)         | serial port parity settings          |

### Examples

| Field        | Value  | Hex    |
| ------------ | ------ | ------ |
| command id   | `9`    | `0x09` |
| command size | `4`    | `0x04` |
| request id   | `52`   | `0x34` |
| baud rate    | `9600` | `0x05` |
| data bits    | `8`    | `0x08` |
| parity       | `odd`  | `0x01` |

Message hex dump: `09 04 34 05 08 01`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x0a`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `10`  | `0x0a` |
| command size | `1`   | `0x01` |
| request id   | `32`  | `0x20` |

Message hex dump: `0a 01 20`


#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description   |
| ----------- | ------------- |
| `3`         | Format error. |


## See also

* [baud rate](../types.md#baud-rate)
* [data bits](../types.md#data-bits)
* [parity](../types.md#parity)
* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
