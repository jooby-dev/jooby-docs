# SetLorawanActivationMethod

Request/response to set the Lorawan activation method OTAA or ABP.


## Request

### Format

| Size | Type                                                       | Field                              |
| ---- | ---------------------------------------------------------- | ---------------------------------- |
| `1`  | `uint8`                                                    | command id = `0x24`                |
| `1`  | `uint8`                                                    | command size                       |
| `1`  | [Request ID](../types.md#request-id)                       | request/response unique identifier |
| `1`  | [Activation method](../types.md#lorawan-activation-method) | LoRaWAN activation method          |


### Examples

| Field             | Value | Hex    |
| ----------------- | ----- | ------ |
| command id        | `36`  | `0x24` |
| command size      | `2`   | `0x02` |
| request id        | `7`   | `0x07` |
| activation method | `1`   | `0x01` |

Message hex dump: `24 02 07 01`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x25`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

#### success:

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `37`  | `0x25` |
| command size | `1`   | `0x01` |
| request id   | `156` | `0x9c` |

Message hex dump: `25 01 9c`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description   |
| ----------- | ------------- |
| `3`         | Format error. |


## See also

* [Request ID](../types.md#request-id)
* [Activation method](../types.md#lorawan-activation-method)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
