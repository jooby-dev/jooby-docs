# ReadArchive

Request/response to get archive data.


## Request

### Format

| Size | Type                                 | Mandatory/optional | Field                                                   |
| ---- | ------------------------------------ | ------------------ | ------------------------------------------------------- |
| `1`  | `byte`                               | mandatory          | command id = `0x11`                                     |
| `1`  | `byte`                               | mandatory          | command size                                            |
| `1`  | [Request ID](../types.md#request-id) | mandatory          | request/response unique identifier                      |
| `1`  | `byte`                               | mandatory          | archive type: <br> `1` - archive 1 <br> `2` - archive 2 |
| `1`  | `byte`                               | mandatory          | index of the first record to get                        |
| `1`  | `byte`                               | optional           | meter unique identifier                                 |
| `4`  | [Time 2000](../types.md#time-2000)   | optional           | Date of the archive records to read                     |

If meter id field is provided, the observer will respond with records from that specified meter.
If meter id field is not provided, the observer will respond with records from all meters.

The date field specifies a specific time within a day. For example, if the field indicates `14:10`, the response will include all the archived data captured from the start of the nearest archive period to `14:10` until the end of that same archive period.
If date field is provided, the observer will respond with records with that specified date.
If date field is not provided, the observer will respond with records regardless of the date.


### Examples

#### request without the meter id and date

| Field        | Value       | Hex    |
| ------------ | ----------- | ------ |
| command id   | `17`        | `0x11` |
| command size | `3`         | `0x03` |
| request id   | `33`        | `0x21` |
| archive type | `Archive 1` | `0x01` |
| start index  | `0`         | `0x00` |

Message hex dump: `11 03 21 01 00`

#### request with the meter id

| Field        | Value       | Hex    |
| ------------ | ----------- | ------ |
| command id   | `17`        | `0x11` |
| command size | `4`         | `0x04` |
| request id   | `33`        | `0x21` |
| archive type | `Archive 1` | `0x01` |
| start index  | `0`         | `0x00` |
| meter id     | `2`         | `0x02` |

Message hex dump: `11 04 21 01 00 02`

#### request with the meter id and date

| Field        | Value                     | Hex          |
| ------------ | ------------------------- | ------------ |
| command id   | `17`                      | `0x11`       |
| command size | `4`                       | `0x04`       |
| request id   | `33`                      | `0x21`       |
| archive type | `Archive 1`               | `0x01`       |
| start index  | `0`                       | `0x00`       |
| meter id     | `2`                       | `0x02`       |
| time         | `2023.12.23 00:00:00 GMT` | `0x2d18df80` |

Message hex dump: `11 08 21 01 00 02 2d 18 df 80`


## Response

### Format

| Size | Type                                 | Field                                            |
| ---- | ------------------------------------ | ------------------------------------------------ |
| `1`  | `byte`                               | command id = `0x12`                              |
| `1`  | `byte`                               | command size (dynamic, `3+`)                     |
| `1`  | [Request ID](../types.md#request-id) | request/response unique identifier               |
| `1`  | `byte`                               | is data completed                                |
| `1`  | `byte`                               | meter unique identifier                          |
| `4`  | [Time 2000](../types.md#time-2000)   | the date and time at which the data was captured |
| `1`  | [OBIS ID](../types.md#obis-id)       | OBIS ID `1`                                      |
| `4`  | `float32`                            | OBIS content `1`                                 |
| ...  | ...                                  | ...                                              |
| `1`  | [OBIS ID](../types.md#obis-od)       | OBIS ID `N`                                      |
| `4`  | `float32`                            | OBIS content `N`                                 |

Note: the date and time in response can be different from the corresponding time field in request.

### Examples

| Field             | Value                     | Hex          |
| ----------------- | ------------------------- | ------------ |
| command id        | `18`                      | `0x12`       |
| command size      | `17`                      | `0x11`       |
| request id        | `34`                      | `0x22`       |
| is data completed | `1`                       | `0x01`       |
| meter id          | `1`                       | `0x01`       |
| time              | `2023.12.23 04:00:00 GMT` | `0x2d1917c0` |
| OBIS ID `1`       | `50`                      | `0x32`       |
| OBIS content `1`  | `22.27`                   | `0x41b228f6` |
| OBIS ID `2`       | `56`                      | `0x38`       |
| OBIS content `2`  | `89.33`                   | `0x42b2a8f6` |

Message hex dump: `12 11 22 01 01 2d 19 17 c0 32 41 b2 28 f6 38 42 b2 a8 f6`


## See also

* [Request ID](../types.md#request-id)
* [Meter ID](../types.md#meter-id)
* [Time 2000](../types.md#time-2000)
* [OBIS ID](../types.md#obis-id)
