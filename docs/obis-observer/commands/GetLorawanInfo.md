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
| `1`  | [Connection method](../types.md#lorawan-connection-method) | LoRaWAN connection method |

### Examples

#### LoRaWAN information:

| Field                 | Value              | Hex                  |
| --------------------- | ------------------ | -------------------- |
| command id            | `31`               | `0x1f`               |
| request id            | `7`                | `0x07`               |
| device EUI            | `001a798816aa5561` | `0x001a798816aa5561` |
| application EUI       | `0011223344556677` | `0x0011223344556677` | 
| connection method     | `1`                | `0x01`               |

Message hex dump: `1f 07 00 1a 79 88 16 aa 55 61 00 11 22 33 44 55 66 77 01`


## See also

* [Request ID](../types.md#request-id)
* [Connection method](../types.md#LoRaWAN-connection-method)
