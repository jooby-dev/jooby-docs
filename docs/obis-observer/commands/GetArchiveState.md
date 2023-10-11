# GetArchiveState

Request/response to get the archive state for the specific meter, including the record count, eldest record date, and newest record date.


## Request

### Format

| Size | Type                                 | Mandatory/optional | Field                                                   |
| ---- | ------------------------------------ | ------------------ | ------------------------------------------------------- |
| `1`  | `byte`                               | mandatory          | command id = `0x0f`                                     |
| `1`  | `byte`                               | mandatory          | command size (dynamic, `2+`)                            |
| `1`  | [Request ID](../types.md#request-id) | mandatory          | request/response unique identifier                      |
| `1`  | `byte`                               | mandatory          | archive type: <br> `1` - archive 1 <br> `2` - archive 2 |
| `1`  | [Meter ID](../types.md#meter-id)     | optional           | meter unique identifier                                 |

If meter id field is provided, the observer will respond with information about that specified meter.
If meter id field is not provided, the observer will respond with information about all meters.


### Examples

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `15`  | `0x0f` |
| command size | `3`   | `0x03` |
| request id   | `41`  | `0x29` |
| archive type | `1`   | `0x01` |
| meter id     | `3`   | `0x03` |

Message hex dump: `0f 03 29 01 03`


## Response

### Format

| Size | Type                                 | Field                                  |
| ---- | ------------------------------------ | -------------------------------------- |
| `1`  | `byte`                               | command id = `0x10`                    |
| `1`  | `byte`                               | command size                           |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier     |
| `4`  | `uint32_be`                          | number of the archive records          |
| `4`  | [Time 2000](../types.md#time-2000)   | the date of the eldest archive records |
| `4`  | [Time 2000](../types.md#time-2000)   | the date of the newest archive records |


### Examples

#### no archive records

| Field        | Value | Hex    |
| ------------ | ----- | ------ |
| command id   | `16`  | `0x10` |
| command size | `1`   | `0x01` |
| request id   | `2`   | `0x02` |

Message hex dump: `10 01 02`

#### some archive records are present

| Field              | Value                     | Hex          |
| ------------------ | ------------------------- | ------------ |
| command id         | `16`                      | `0x10`       |
| command size       | `13`                      | `0x0d`       |
| request id         | `2`                       | `0x02`       |
| records number     | `81`                      | `0x00000051` |
| eldest record time | `2023.06.27 18:45:02 GMT` | `0x2c2deaae` |
| newest record time | `2023.06.28 15:15:02 GMT` | `0x2c2f0af6` |

Message hex dump: `10 0d 02 00 00 00 51 2c 2d ea ae 2c 2f 0a f6`

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
