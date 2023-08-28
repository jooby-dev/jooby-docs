# SetLorawanActivationMethod

Request/response to set the Lorawan activation method OTAA or ABP.


## Request

### Format

| Size | Type                                                       | Field                              |
| ---- | ---------------------------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                                     | command id = `0x17`                |
| `1`  | `byte`                                                     | command size                       |
| `1`  | [Request ID](../types.md#request-id)                       | request/response unique identifier |
| `1`  | [Activation method](../types.md#lorawan-activation-method) | LoRaWAN activation method          |


### Examples

| Field             | Value | Hex    |
| ----------------- | ----- | ------ |
| command id        | `23`  | `0x17` |
| command size      | `2`   | `0x02` |
| request id        | `7`   | `0x07` |
| activation method | `1`   | `0x01` |

Message hex dump: `17 02 07 01`


## Response

### Format

| Size | Type                                   | Field                              |
| ---- | -------------------------------------- | ---------------------------------- |
| `1`  | `byte`                                 | command id = `0x18`                |
| `1`  | `byte`                                 | command size                       |
| `1`  | [Request ID](../types.md#request-id)   | request/response unique identifier |
| `1`  | [Result code](../types.md#result-code) | operation result code              |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `24`  | `0x18` |
| command size | `2`   | `0x02` |
| request id   | `156` | `0x9c` |
| result code  | `OK`  | `0x00` |

Message hex dump: `18 02 9c 00`


### Result codes:

| Result code | Description                                                |
| ----------- | ---------------------------------------------------------- |
| `0`         | Ok. The Operation was successful.                          |


## See also

* [Request ID](../types.md#request-id)
* [Result code](../types.md#result-code)
* [Activation method](../types.md#lorawan-activation-method)
