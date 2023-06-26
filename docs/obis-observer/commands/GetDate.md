# GetDate

Request/response to get the current date and time on the device.


## Request

### Format

| Size  | Type                                 | Field                              |
| ----- | ------------------------------------ | ---------------------------------- |
| `1`   | `byte`                               | command id = `0x22`                |
| `1`   | [Request ID](../types.md#request-id) | request/response unique identifier |

### Examples

| Field      | Value | Hex    |
| ---------- | ----- | ------ |
| command id | `34`  | `0x22` |
| request id | `18`  | `0x12` |

Message hex dump: `22 12`


## Response

### Format

| Size | Type                                 | Field                                            |
| ---- | ------------------------------------ | ------------------------------------------------ |
| `1`  | `byte`                               | command id = `0x23`                              |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier               |
| `4`  | [Time 2000](../types.md#time-2000)   | The field specifies a current time on the device |
| `4`  | `uint32_be`                          | uptime in seconds                                |



### Examples

#### Device information:

| Field             | Value                   | Hex          |
| ----------------- | ----------------------- | ------------ |
| command id        | `35`                    | `0x23`       |
| request id        | `7`                     | `0x07`       |
| time              | `26.06.23 11:50:11 GMT` | `0x31cd2f73` |
| uptime in seconds | `4016`                  | `0x00000fb0` |

Message hex dump: `23 07 31 cd 2f 73 00 00 0f b0`


## See also

* [Request ID](../types.md#request-id)
* [String](../types.md#time-2000)
