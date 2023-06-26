# GetReadoutState

Request/response to get the readout related state and statistic.


## Request

### Format

| Size  | Type                                 | Field                              |
| ----- | ------------------------------------ | ---------------------------------- |
| `1`   | `byte`                               | command id = `0x26`                |
| `1`   | [Request ID](../types.md#request-id) | request/response unique identifier |

### Examples

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `38`  | `0x26` |
| request id | `18`  | `0x12` |

Message hex dump: `26 12`


## Response

### Format

| Size | Type                                 | Field                                                                                                   |
| ---- | ------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x27`                                                                                     |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                                                                      |
| `4`  | uint32_be                            | elapsed time in seconds since the start of the device when the last successful readout attempt occurred |
| `4`  | uint32_be                            | elapsed time in seconds since the start of the device when the last failed readout attempt occurred     |
| `1`  | `byte`                               | success readout attempts in percent                                                                     |
| `1`  | `byte`                               | the count of the 'WAIT NEXT SYMBOL' errors                                                              |
| `1`  | `byte`                               | the count of the 'WAIT ID' errors                                                                       |
| `1`  | `byte`                               | the count of the 'WAIT NEXT STATE' errors                                                               |
| `1`  | `byte`                               | the count of the 'WRONG BCC' errors                                                                     |
| `1`  | `byte`                               | the count of the parity errors                                                                          |
| `1`  | `byte`                               | the count of the frame errors                                                                           |
| `1`  | `byte`                               | the count of the overrun errors                                                                         |


### Examples

| Field                                                                                                   | Value | Hex          |
| ------------------------------------------------------------------------------------------------------- | ----- | ------------ |
| command id                                                                                              | `37`  | `0x25`       |
| request id                                                                                              | `3`   | `0x03`       |
| elapsed time in seconds since the start of the device when the last successful readout attempt occurred | `127` | `0x0000007f` |
| elapsed time in seconds since the start of the device when the last failed readout attempt occurred     | `193` | `0x00000000` |
| success readout attempts in percent                                                                     | `100` | `0x64`       |
| the count of the 'WAIT NEXT SYMBOL' errors                                                              | `0`   | `0x00`       |
| the count of the 'WAIT ID' errors                                                                       | `0`   | `0x00`       |
| the count of the 'WAIT NEXT STATE' errors                                                               | `0`   | `0x00`       |
| the count of the 'WRONG BCC' errors                                                                     | `0`   | `0x00`       |
| the count of the parity errors                                                                          | `0`   | `0x00`       |
| the count of the frame errors                                                                           | `0`   | `0x00`       |
| the count of the overrun errors                                                                         | `0`   | `0x00`       |

Message hex dump: `27 03 00 00 00 7f 00 00 00 00 64 00 00 00 00 00 00 00`


## See also

* [Request ID](../types.md#request-id)
