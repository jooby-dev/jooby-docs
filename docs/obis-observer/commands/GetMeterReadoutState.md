# GetReadoutState

Request/response to get the readout related state and statistic.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x26`                |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |

### Examples

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `38`  | `0x26` |
| request id | `18`  | `0x12` |

Message hex dump: `26 12`


## Response

### Format

| Size | Type                                 | Field                                                                                   |
| ---- | ------------------------------------ | --------------------------------------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x27`                                                                     |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                                      |
| `4`  | `uint32_be`                          | seconds since the start of the device when the last successful readout attempt occurred |
| `4`  | `uint32_be`                          | seconds since the start of the device when the last failed readout attempt occurred     |
| `2`  | `uint16_be`                          | the number of the readout attempts                                                      |
| `2`  | `uint16_be`                          | the number of the successful readout attempts                                           |
| `2`  | `uint16_be`                          | the number of the readout repetitions                                                   |
| `1`  | `byte`                               | the number of the `WAIT NEXT SYMBOL` errors                                             |
| `1`  | `byte`                               | the number of the `WAIT ID` errors                                                      |
| `1`  | `byte`                               | the number of the `WAIT NEXT STATE` errors                                              |
| `1`  | `byte`                               | the number of the `WRONG BCC` errors                                                    |
| `1`  | `byte`                               | the number of the parity errors                                                         |
| `1`  | `byte`                               | the number of the frame errors                                                          |
| `1`  | `byte`                               | the number of the overrun errors                                                        |


### Examples

| Field                                                                                   | Value | Hex          |
| ----------------------------------------------------------------------------------------| ----- | ------------ |
| command id                                                                              | `39`  | `0x27`       |
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

Message hex dump: `27 03 00 00 00 7f 00 00 00 c1 00 0e 00 0c 00 02 00 00 00 00 00 00 00`


## See also

* [Request ID](../types.md#request-id)
