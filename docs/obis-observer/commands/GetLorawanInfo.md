# GetLorawanInfo

Request/response the LoRaWAN information, like device EUI, application EUI and connection method.


## Request

### Format

| Size  | Type                                 | Field                              |
| ----- | ------------------------------------ | ---------------------------------- |
| `1`   | `byte`                               | command id = `0x1e`                |
| `1`   | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### get LoRaWAN information:

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `30`  | `0x1e` |
| request id | `3`   | `0x03` |

Message hex dump: `1e 03`


## Response

### Format

| Size | Type                                 | Field                                           |
| ---- | ------------------------------------ | ----------------------------------------------- |
| `1`  | `byte`                               | command id = `0x1f`                             |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier              |
| `8`  | `byte`                               | device EUI                                      |
| `8`  | `byte`                               | application EUI                                 |
| `1`  | [Connection method](../types.md#LoRaWAN-connection-method) | LoRaWAN connection method |

### Examples

#### LoRaWAN information:

| Field                 | Value | Hex    |
| --------------------- | ----- | ------ |
| command id            | `31   | `0x1f` |
| request id            | `7`   | `0x07` |
| device EUI            | `[0x00, 0x1a, 0x79, 0x88, 0x16, 0xaa, 0x55, 0x61]` | |
| application EUI       | `[0x00, 0x11, 0x22, 0x33, 0x44, 0x55, 0x66, 0x77]` | |
| Connection method `1` | `1`   | `0x01` |

Message hex dump: `1f 07 00 1a 79 88 16 aa 55 61 00 11 22 33 44 55 66 77 01`


## See also

* [Request ID](../types.md#request-id)
* [Connection method](../types.md#LoRaWAN-connection-method)
