# GetMeterArchiveState

Request/response to get the archive state for the specific meter, including the record count, eldest record date, and newest record date.


## Request

### Format

| Size | Type                                 | Field                                                   |
| ---- | ------------------------------------ | ------------------------------------------------------- |
| `1`  | `byte`                               | command id = `0x7c`                                     |
| `1`  | `byte`                               | command size                                            |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier                      |
| `1`  | [Meter id](../types.md#meter-id)     | meter unique identifier                                 |
| `1`  | `byte`                               | archive type: <br> `1` - archive 1 <br> `2` - archive 2 |

### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `124` | `0x7c` |
| command size | `3`   | `0x03` |
| request id   | `41`  | `0x29` |
| meter id     | `3`   | `0x03` |
| archive type | `1`   | `0x01` |



Message hex dump: `7c 03 29 03 01`


## Response

### Format

| Size | Type                                 | Field                                  |
| ---- | ------------------------------------ | -------------------------------------- |
| `1`  | `byte`                               | command id = `0x7b`                    |
| `1`  | `byte`                               | command size                           |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier     |
| `4`  | `uint32_be`                          | number of the archive records          |
| `4`  | [Time 2000](../types.md#time-2000)   | the date of the eldest archive records |
| `4`  | [Time 2000](../types.md#time-2000)   | the date of the newest archive records |


### Examples

#### no archive records

| Field          | Value | Hex          |
| -------------- | ----- | ------------ |
| command id     | `125` | `0x7b`       |
| command size   | `5`   | `0x05`       |
| request id     | `2`   | `0x02`       |
| records number | `0`   | `0x00000000` |

Message hex dump: `7b 05 02 00 00 00 00`

#### some archive records are present

| Field              | Value                     | Hex          |
| ------------------ | ------------------------- | ------------ |
| command id         | `125`                     | `0x7b`       |
| command size       | `13`                      | `0x0d`       |
| request id         | `2`                       | `0x02`       |
| records number     | `81`                      | `0x00000051` |
| eldest record time | `2023.06.27 18:45:02 GMT` | `0x2c2deaae` |
| newest record time | `2023.06.28 15:15:02 GMT` | `0x2c2f0af6` |

Message hex dump: `7b 0d 02 00 00 00 51 2c 2d ea ae 2c 2f 0a f6`


## See also

* [Request ID](../types.md#request-id)
* [Meter id](../types.md#meter-id)
* [Time 2000](../types.md#time-2000)
