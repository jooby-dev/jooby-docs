# GetLorawanState

Request/response to get the Lorawan related state and statistic.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x22`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `34`  | `0x22` |
| command size | `1`   | `0x01` |
| request id   | `18`  | `0x12` |

Message hex dump: `22 01 12`


## Response

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x23`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `1`  | `uint8`                              | downlink quality in percent        |
| `1`  | `uint8`                              | RSSI of the last frame             |
| `1`  | `uint8`                              | SNR of the last frame              |
| `1`  | `uint8`                              | device's margin                    |
| `1`  | `uint8`                              | gate's margin                      |
| `1`  | `uint8`                              | reset flag                         |
| `1`  | `uint8`                              | sender collision                   |


### Examples

| Field                       | Value | Hex    |
| --------------------------- | ----- | ------ |
| command id                  | `35`  | `0x23` |
| command size                | `8`   | `0x08` |
| request id                  | `1`   | `0x01` |
| downlink quality in percent | `1`   | `0x01` |
| RSSI of the last frame      | `193` | `0xc1` |
| SNR of the last frame       | `5`   | `0x05` |
| device's margin             | `6`   | `0x06` |
| gate's margin               | `0`   | `0x00` |
| reset flag                  | `0`   | `0x00` |
| sender collision            | `0`   | `0x00` |

Message hex dump: `23 08 01 01 c1 05 06 00 00 00`


## See also

* [Request ID](../types.md#request-id)
