# GeMeterDate

Request/response to get the current date and time on the specific meter.


## Request

### Format

| Size | Type                                 | Field                              |
| ---- | ------------------------------------ | ---------------------------------- |
| `1`  | `byte`                               | command id = `0x7a`                |
| `1`  | `byte`                               | command size                       |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier |
| `4`  | [Meter ID](../types.md#meter-id)     | meter unique identifier            |

### Examples

| Field        | Value | Hex          |
| ------------ | ----- | ------------ |
| command id   | `122` | `0x7a`       |
| command size | `5`   | `0x05`       |
| request id   | `18`  | `0x12`       |
| meter id     | `1`   | `0x00000001` |

Message hex dump: `7a 05 12 00 00 00 01`


## Response

### Format

| Size | Type                                 | Field                                           |
| ---- | ------------------------------------ | ----------------------------------------------- |
| `1`  | `byte`                               | command id = `0x7b`                             |
| `1`  | `byte`                               | command size                                    |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier              |
| `4`  | [Time 2000](../types.md#time-2000)   | The field specifies a current time on the meter |


### Examples

| Field        | Value                     | Hex          |
| ------------ | ------------------------- | ------------ |
| command id   | `123`                     | `0x7b`       |
| command size | `2`                       | `0x02`       |
| request id   | `7`                       | `0x07`       |
| time         | `2023.06.28 15:15:02 GMT` | `0x2c2f0af6` |


Message hex dump: `7b 05 07 2c 2f 0a f6`

#### error:

If an error occurs, the observer will respond by sending the [Error](./uplink/Error.md) command.

##### Result codes:

| Result code | Description          |
| ----------- | -------------------- |
| `3`         | Format error.        |
| `9`         | The meter not found. |


## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
* [Time 2000](../types.md#time-2000)
* [Result code](../types.md#result-code)
* [Error](./uplink/Error.md)
