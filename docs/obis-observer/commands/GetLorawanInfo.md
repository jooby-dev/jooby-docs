# GetLorawanInfo

Request/response the LoRaWAN information, like device EUI, application EUI and activation method.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x13`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `19`  | `0x13` |
| command size | `1`   | `0x01` |
| request id   | `3`   | `0x03` |

Message hex dump: `13 01 03`


## Response

### Format

| Size | Type                                                       | Field                              |
| ---- | ---------------------------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                                     | command id = `0x14`                |
| `1`  | `byte`                                                     | command size                       |
| `1`  | [Request ID](../types.md#request-id)                       | request/response unique identifier |
| `8`  | `byte`                                                     | device EUI                         |
| `8`  | `byte`                                                     | application EUI                    |
| `1`  | [Device class](../types.md#lorawan-device-classes)         | LoRaWAN device classes             |
| `1`  | [Activation method](../types.md#lorawan-activation-method) | LoRaWAN activation method          |


### Examples

| Field             | Value              | Hex                  |
| ----------------- | ------------------ | -------------------- |
| command id        | `20`               | `0x14`               |
| command size      | `19`               | `0x13`               |
| request id        | `7`                | `0x07`               |
| device EUI        | `001a798816aa5561` | `0x001a798816aa5561` |
| application EUI   | `0011223344556677` | `0x0011223344556677` |
| device class      | `C`                | `0x02`               |
| activation method | `1`                | `0x01`               |

Message hex dump: `14 13 07 00 1a 79 88 16 aa 55 61 00 11 22 33 44 55 66 77 02 01`


## See also

* [Request ID](../types.md#request-id)
* [Device class](../types.md#lorawan-device-classes)
* [Activation method](../types.md#lorawan-activation-method)
