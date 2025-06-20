# GetMeterReadoutState

Request/response to get the readout related state and statistic from the specific meter.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `uint8`                              | command id = `0x81`                |
| `1`  | `uint8`                              | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `4`  | [Meter ID](../types.md#meter-id)     | meter unique identifier            |

### Examples

#### get readout state for meter with id `8`:

| Field        | Value | Hex          |
| ------------ | ----- | ------------ |
| command id   | `129` | `0x81`       |
| command size | `5`   | `0x05`       |
| request id   | `18`  | `0x12`       |
| meter id     | `8`   | `0x00000008` |

Message hex dump: `81 05 12 00 00 00 08`



## Response

### Format

| Size | Type                                 | Field                                                                                   |
| ---- | ------------------------------------ | --------------------------------------------------------------------------------------- |
| `1`  | `uint8`                              | command id = `0x82`                                                                     |
| `1`  | `uint8`                              | command size                                                                            |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                                      |
| `4`  | `uint32_be`                          | seconds since the start of the device when the last successful readout attempt occurred |
| `4`  | `uint32_be`                          | seconds since the start of the device when the last failed readout attempt occurred     |
| `2`  | `uint16_be`                          | the number of the readout attempts                                                      |
| `2`  | `uint16_be`                          | the number of the successful readout attempts                                           |
| `2`  | `uint16_be`                          | the number of the readout repetitions                                                   |
| `1`  | `uint8`                              | the number of the `WAIT NEXT SYMBOL` errors                                             |
| `1`  | `uint8`                              | the number of the `WAIT ID` errors                                                      |
| `1`  | `uint8`                              | the number of the `WAIT NEXT STATE` errors                                              |
| `1`  | `uint8`                              | the number of the `WRONG BCC` errors                                                    |
| `1`  | `uint8`                              | the number of the parity errors                                                         |
| `1`  | `uint8`                              | the number of the frame errors                                                          |
| `1`  | `uint8`                              | the number of the overrun errors                                                        |


### Examples

| Field                                                                                   | Value | Hex          |
| --------------------------------------------------------------------------------------- | ----- | ------------ |
| command id                                                                              | `130` | `0x82`       |
| command size                                                                            | `22`  | `0x16`       |
| request id                                                                              | `3`   | `0x03`       |
| seconds since the start of the device when the last successful readout attempt occurred | `127` | `0x0000007f` |
| seconds since the start of the device when the last failed readout attempt occurred     | `193` | `0x000000c1` |
| the number of the readout attempts                                                      | `14`  | `0x0e`       |
| the number of the successful readout attempts                                           | `12`  | `0x0c`       |
| the number of the readout repetitions                                                   | `2`   | `0x02`       |
| the number of the `WAIT NEXT SYMBOL` errors                                             | `0`   | `0x00`       |
| the number of the `WAIT ID` errors                                                      | `0`   | `0x00`       |
| the number of the `WAIT NEXT STATE` errors                                              | `0`   | `0x00`       |
| the number of the `WRONG BCC` errors                                                    | `0`   | `0x00`       |
| the number of the parity errors                                                         | `0`   | `0x00`       |
| the number of the frame errors                                                          | `0`   | `0x00`       |
| the number of the overrun errors                                                        | `0`   | `0x00`       |

Message hex dump: `82 16 03 00 00 00 7f 00 00 00 c1 00 0e 00 0c 00 02 00 00 00 00 00 00 00`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### result codes:

| Result code | Description          |
| ----------- | -------------------- |
| `3`         | Format error.        |
| `9`         | The meter not found. |

## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
